---
title: Ponto de extremidade de metadados seguros personalizados
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2baa99ddaf5de60407b233b5a6ea013ad87401f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508055"
---
# <a name="custom-secure-metadata-endpoint"></a>Ponto de extremidade de metadados seguros personalizados
Este exemplo demonstra como implementar um serviço com um ponto de extremidade de metadados seguro que usa uma das associações não-metadata exchange e como configurar [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou clientes para buscar o metadados de tal um ponto de extremidade de metadados. Há duas associações fornecidas pelo sistema disponíveis para expor pontos de extremidade de metadados: mexHttpBinding e mexHttpsBinding. mexHttpBinding é usado para expor um ponto de extremidade de metadados sobre HTTP de forma não segura. mexHttpsBinding é usado para expor um ponto de extremidade de metadados via HTTPS de forma segura. Este exemplo mostra como expor um ponto de extremidade de metadados seguro usando o <xref:System.ServiceModel.WSHttpBinding>. Você deseja fazer isso quando você deseja alterar as configurações de segurança na associação, mas você não deseja usar HTTPS. Se você usar o mexHttpsBinding seu ponto de extremidade de metadados será seguro, mas não é possível modificar as configurações de associação.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="service"></a>Serviço  
 O serviço neste exemplo tem dois pontos de extremidade. O ponto de extremidade do aplicativo serve a `ICalculator` contrato em um `WSHttpBinding` com `ReliableSession` habilitado e `Message` usando certificados de segurança. Também usa o ponto de extremidade de metadados `WSHttpBinding`, com as mesmas configurações de segurança, mas sem nenhum `ReliableSession`. Aqui está a configuração relevante:  
  
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
  
 Em muitos outros exemplos, o ponto de extremidade de metadados usa o padrão `mexHttpBinding`, que não é seguro. Aqui os metadados é protegido usando `WSHttpBinding` com `Message` segurança. Em ordem para clientes de metadados recuperar esses metadados, eles devem ser configurados com uma associação correspondente. Este exemplo demonstra duas tais clientes.  
  
 O primeiro cliente usa o Svcutil.exe para buscar os metadados e gerar o código do cliente e configuração em tempo de design. Como o serviço usa uma associação não-padrão para os metadados, a ferramenta Svcutil.exe deve ser configurada especificamente para que ele possa obter os metadados do serviço usando essa associação.  
  
 O segundo cliente usa o `MetadataResolver` buscar dinamicamente os metadados de um contrato conhecido e, em seguida, invocar operações no cliente gerado dinamicamente.  
  
## <a name="svcutil-client"></a>Cliente svcutil  
 Ao usar a associação padrão para hospedar seu `IMetadataExchange` ponto de extremidade, você pode executar o Svcutil.exe com o endereço do ponto de extremidade:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 e ele funciona. Mas, neste exemplo, o servidor usa um ponto de extremidade não padrão para hospedar os metadados. Para que Svcutil.exe deve ser instruído a usar a associação correta. Isso pode ser feito usando um arquivo de Svcutil.exe.config.  
  
 O arquivo Svcutil.exe.config se parece com um arquivo de configuração de cliente normal. Os aspectos incomuns só são o nome do ponto de extremidade de cliente e o contrato:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 O nome do ponto de extremidade deve ser o nome do esquema de endereço em que os metadados é hospedado e o contrato de ponto de extremidade deve ser `IMetadataExchange`. Portanto, quando Svcutil.exe é executado com uma linha de comando, como o seguinte:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ele procura por ponto de extremidade chamado "http" e um contrato `IMetadataExchange` para configurar a associação e o comportamento da troca de comunicação com o ponto de extremidade de metadados. O restante do arquivo Svcutil.exe.config no exemplo especifica a configuração de associação e credenciais de comportamento para coincidir com a configuração do servidor do ponto de extremidade de metadados.  
  
 Em ordem para o Svcutil.exe escolher a configuração no Svcutil.exe.config, Svcutil.exe deve estar no mesmo diretório que o arquivo de configuração. Como resultado, você deverá copiar o Svcutil.exe de seu local de instalação para o diretório que contém o arquivo Svcutil.exe.config. Nesse diretório, execute o seguinte comando:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 O principal ". \\"garante que a cópia do Svcutil.exe neste diretório (aquele que tem um Svcutil.exe.config correspondente) é executada.  
  
## <a name="metadataresolver-client"></a>Cliente MetadataResolver  
 Se o cliente sabe como se comunicar com os metadados em tempo de design e o contrato, o cliente possa encontrar dinamicamente a associação e o endereço dos pontos de extremidade do aplicativo usando o `MetadataResolver`. Esse cliente de exemplo demonstra isso, mostrando como configurar a associação e as credenciais usadas pelo `MetadataResolver` criando e configurando um `MetadataExchangeClient`.  
  
 As mesmas informações de associação e o certificado que eram exibidos no Svcutil.exe.config podem ser especificadas imperativa o `MetadataExchangeClient`:  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 Com o `mexClient` configurado, pode enumerar os contratos que estamos interessados em e usar `MetadataResolver` para obter uma lista de pontos de extremidade com esses contratos:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Finalmente, pode usar as informações esses pontos de extremidade de inicializar a associação e o endereço de um `ChannelFactory` usado para criar canais para se comunicar com os pontos de extremidade do aplicativo.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 O ponto-chave desse cliente de exemplo é demonstrar que, se você estiver usando `MetadataResolver`e você deve especificar associações personalizadas ou comportamentos para a comunicação de troca de metadados, você pode usar um `MetadataExchangeClient` para especificar as configurações personalizadas.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e criar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo no mesmo computador  
  
1.  Execute bat da pasta de instalação do exemplo. Isso instala todos os certificados necessários para executar o exemplo. Observe que bat usa a ferramenta de FindPrivateKey.exe, que está instalada executando setupCertTool.bat de [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Execute o aplicativo cliente de \MetadataResolverClient\bin ou \SvcutilClient\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
3.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
4.  Remova os certificados executando Cleanup.bat quando você tiver terminado com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
#### <a name="to-run-the-sample-across-machines"></a>Para executar o exemplo em computadores  
  
1.  No servidor, execute `setup.bat service`. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
2.  No servidor, edite o Web. config para refletir o novo nome do certificado. Ou seja, alterar o `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elemento para o nome de domínio totalmente qualificado do computador.  
  
3.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
4.  No cliente, execute `setup.bat client`. Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado Client.com e exporta o certificado de cliente para um arquivo chamado cer.  
  
5.  No arquivo App. config do `MetadataResolverClient` no computador cliente, altere o valor do endereço do ponto de extremidade mex para coincidir com o novo endereço do seu serviço. Para fazer isso, substituindo o host local com o nome de domínio totalmente qualificado do servidor. Altere também a ocorrência de "localhost" no arquivo metadataResolverClient.cs para o novo nome de certificado de serviço (o nome de domínio totalmente qualificado do servidor). Faça o mesmo com o App. config do projeto SvcutilClient.  
  
6.  Copie o arquivo CER do diretório do cliente para o diretório de serviço no servidor.  
  
7.  No cliente, execute `ImportServiceCert.bat`. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.  
  
8.  No servidor, execute `ImportClientCert.bat`, isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.  
  
9. No computador do serviço, compilar o projeto de serviço no Visual Studio e selecione a página de Ajuda em um navegador da web para verificar se ele está em execução.  
  
10. No computador cliente, execute o MetadataResolverClient ou o SvcutilClient do VS.  
  
    1.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
-   Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a>Consulte também
