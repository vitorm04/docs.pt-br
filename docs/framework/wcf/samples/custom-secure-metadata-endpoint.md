---
title: Ponto de extremidade de metadados seguros personalizados
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 89f12b4490d556884aaa15dcb102b5ad876707ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183842"
---
# <a name="custom-secure-metadata-endpoint"></a>Ponto de extremidade de metadados seguros personalizados
Esta amostra demonstra como implementar um serviço com um ponto final de metadados seguro que usa uma das vinculações de troca de metadados e como configurar [o ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou os clientes para buscar os metadados a partir de um ponto final de metadados. Existem duas vinculações fornecidas pelo sistema disponíveis para expor pontos finais de metadados: mexHttpBinding e mexHttpsBinding. mexHttpBinding é usado para expor um ponto final de metadados sobre HTTP de forma não segura. mexHttpsBinding é usado para expor um ponto final de metadados sobre HTTPS de forma segura. Esta amostra ilustra como expor um ponto final <xref:System.ServiceModel.WSHttpBinding>de metadados seguro usando o . Você gostaria de fazer isso quando quiser alterar as configurações de segurança na vinculação, mas não deseja usar HTTPS. Se você usar o mexHttpsBinding seu ponto final de metadados será seguro, mas não há como modificar as configurações de vinculação.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
## <a name="service"></a>Serviço  
 O serviço nesta amostra tem dois pontos finais. O ponto final `ICalculator` do aplicativo `WSHttpBinding` `ReliableSession` atende ao `Message` contrato em um com habilitação e segurança usando certificados. O ponto final de `WSHttpBinding`metadados também usa , `ReliableSession`com as mesmas configurações de segurança, mas sem . Aqui está a configuração relevante:  
  
```xml  
<services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 Em muitas das outras amostras, o ponto `mexHttpBinding`final de metadados usa o padrão , que não é seguro. Aqui os metadados `WSHttpBinding` são `Message` protegidos usando com segurança. Para que os clientes de metadados recuperem esses metadados, eles devem ser configurados com uma vinculação correspondente. Esta amostra demonstra dois desses clientes.  
  
 O primeiro cliente usa o Svcutil.exe para buscar os metadados e gerar código e configuração do cliente na hora do projeto. Como o serviço usa uma vinculação não padrão para os metadados, a ferramenta Svcutil.exe deve ser configurada especificamente para que possa obter os metadados do serviço usando essa vinculação.  
  
 O segundo cliente `MetadataResolver` usa o para buscar dinamicamente os metadados para um contrato conhecido e, em seguida, invocar operações no cliente gerado dinamicamente.  
  
## <a name="svcutil-client"></a>Cliente Svcutil  
 Ao usar a vinculação `IMetadataExchange` padrão para hospedar seu ponto final, você pode executar Svcutil.exe com o endereço desse ponto final:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 e funciona. Mas nesta amostra, o servidor usa um ponto final não padrão para hospedar os metadados. Então Svcutil.exe deve ser instruído a usar a ligação correta. Isso pode ser feito usando um arquivo Svcutil.exe.config.  
  
 O arquivo Svcutil.exe.config parece um arquivo de configuração normal do cliente. Os únicos aspectos incomuns são o nome e o contrato do ponto final do cliente:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 O nome do ponto final deve ser o nome do esquema do endereço onde `IMetadataExchange`os metadados estão hospedados e o contrato de ponto final deve ser . Assim, quando Svcutil.exe é executado com uma linha de comando como o seguinte:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ele procura o ponto final chamado `IMetadataExchange` "http" e contrato para configurar a vinculação e o comportamento da troca de comunicação com o ponto final de metadados. O resto do arquivo Svcutil.exe.config na amostra especifica as credenciais de configuração e comportamento de vinculação para corresponder à configuração do ponto final do ponto final do ponto final do servidor.  
  
 Para que o Svcutil.exe pegue a configuração em Svcutil.exe.config, o Svcutil.exe deve estar no mesmo diretório que o arquivo de configuração. Como resultado, você deve copiar Svcutil.exe de seu local de instalação para o diretório que contém o arquivo Svcutil.exe.config. Em seguida, a partir desse diretório, execute o seguinte comando:  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 O protagonista". \\" garante que a cópia de Svcutil.exe neste diretório (aquela que tem um Svcutil.exe.config correspondente) seja executada.  
  
## <a name="metadataresolver-client"></a>Cliente MetadataResolver  
 Se o cliente souber o contrato e como falar com os metadados na hora do projeto, o `MetadataResolver`cliente poderá descobrir dinamicamente a vinculação e o endereço dos pontos finais do aplicativo usando o . Este cliente de amostra demonstra isso, mostrando como `MetadataResolver` configurar a vinculação e as credenciais usadas pela criação e configuração de um `MetadataExchangeClient`.  
  
 As mesmas informações de vinculação e certificado sumidas em Svcutil.exe.config podem ser especificadas imperativamente no: `MetadataExchangeClient`  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 Com `mexClient` o configurado, podemos enumerar os contratos que `MetadataResolver` nos interessam, e usar para buscar uma lista de pontos finais com esses contratos:  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Finalmente, podemos usar as informações desses pontos finais para `ChannelFactory` inicializar a vinculação e o endereço de um usado para criar canais para se comunicar com os pontos finais do aplicativo.  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 O ponto chave deste cliente de amostra é `MetadataResolver`demonstrar que, se você estiver usando , e você deve especificar vinculações ou comportamentos personalizados para a comunicação de troca de metadados, você pode usar um `MetadataExchangeClient` para especificar essas configurações personalizadas.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e construir a amostra  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar a amostra na mesma máquina  
  
1. Executar Setup.bat da pasta de instalação de amostra. Isso instala todos os certificados necessários para a execução da amostra. Observe que o Setup.bat usa a ferramenta FindPrivateKey.exe, que é instalada executando a configuraçãoCertTool.bat do [Procedimento de Configuração Única para amostras da Fundação de Comunicação do Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Execute o aplicativo cliente de \MetadataResolverClient\bin ou \SvcutilClient\bin. A atividade do cliente é exibida no aplicativo do console cliente.  
  
3. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Remova os certificados executando Cleanup.bat quando terminar com a amostra. Outras amostras de segurança usam os mesmos certificados.  
  
#### <a name="to-run-the-sample-across-machines"></a>Para executar a amostra através de máquinas  
  
1. No servidor, `setup.bat service`execute. A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado da máquina e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
2. No servidor, edite Web.config para refletir o novo nome do certificado. Ou seja, `findValue` alterar o atributo no [ \<elemento serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) para o nome de domínio totalmente qualificado da máquina.  
  
3. Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente na máquina cliente.  
  
4. No cliente, `setup.bat client`corra. A `setup.bat` execução com o `client` argumento cria um certificado de cliente chamado Client.com e exporta o certificado do cliente para um arquivo chamado Client.cer.  
  
5. No arquivo App.config `MetadataResolverClient` da máquina cliente, altere o valor do endereço do ponto final do mex para corresponder ao novo endereço do seu serviço. Você faz isso substituindo o localhost pelo nome de domínio totalmente qualificado do servidor. Altere também a ocorrência de "localhost" no arquivo metadataResolverClient.cs para o novo nome do certificado de serviço (o nome de domínio totalmente qualificado do servidor). Faça a mesma coisa para o App.config do projeto SvcutilClient.  
  
6. Copie o arquivo Client.cer do diretório do cliente para o diretório de serviço situado no servidor.  
  
7. No cliente, `ImportServiceCert.bat`corra. Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.  
  
8. No servidor, `ImportClientCert.bat`execute , Isso importa o certificado do cliente do arquivo Client.cer para a loja LocalMachine - TrustedPeople.  
  
9. Na máquina de serviço, construa o projeto de serviço no Visual Studio e selecione a página de ajuda em um navegador da Web para verificar se ele está sendo executado.  
  
10. Na máquina cliente, execute o MetadataResolverClient ou o SvcutilClient do VS.  
  
    1. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
- Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.  
  
    > [!NOTE]
    > Este script não remove certificados de serviço em um cliente ao executar esta amostra em máquinas. Se você tiver executado amostras de Windows Communication Foundation (WCF) que usam certificados em máquinas, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople. Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`seguinte comando: . Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
