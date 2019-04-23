---
title: Ponto de extremidade de metadados seguros personalizados
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: c835cfecab38a76f285767f918dfc082915ffcfc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769678"
---
# <a name="custom-secure-metadata-endpoint"></a>Ponto de extremidade de metadados seguros personalizados
Este exemplo demonstra como implementar um serviço com um ponto de extremidade de metadados seguros que usa uma das associações não-metadata exchange e como configurar [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou clientes para buscar o metadados de tal um ponto de extremidade de metadados. Há duas associações fornecidas pelo sistema disponíveis para expor pontos de extremidade de metadados: mexHttpBinding e mexHttpsBinding. mexHttpBinding é usado para expor um ponto de extremidade de metadados sobre HTTP de forma não segura. mexHttpsBinding é usado para expor um ponto de extremidade de metadados via HTTPS de uma maneira segura. Este exemplo ilustra como expor um ponto de extremidade de metadados seguros usando o <xref:System.ServiceModel.WSHttpBinding>. Você pode querer fazer isso quando você deseja alterar as configurações de segurança na associação, mas você não deseja usar HTTPS. Se você usar o mexHttpsBinding seu ponto de extremidade de metadados será seguro, mas não é possível modificar as configurações de associação.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="service"></a>Serviço  
 O serviço neste exemplo tem dois pontos de extremidade. O ponto de extremidade do aplicativo serve os `ICalculator` contrato em um `WSHttpBinding` com `ReliableSession` habilitado e `Message` usando certificados de segurança. Também usa o ponto de extremidade de metadados `WSHttpBinding`, com as mesmas configurações de segurança, mas sem nenhum `ReliableSession`. Aqui está a configuração relevante:  
  
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
  
 O primeiro cliente usa Svcutil.exe para buscar os metadados e gerar código de cliente e a configuração em tempo de design. Como o serviço usa uma associação não-padrão para os metadados, a ferramenta Svcutil.exe deve ser configurada especificamente para que ele possa obter os metadados do serviço usando o que a associação.  
  
 O segundo cliente usa o `MetadataResolver` para buscar dinamicamente os metadados para um contrato a conhecidas e, em seguida, chamar operações no cliente gerado dinamicamente.  
  
## <a name="svcutil-client"></a>Cliente de svcutil  
 Ao usar a associação padrão para hospedar seu `IMetadataExchange` ponto de extremidade, você pode executar Svcutil.exe com o endereço do ponto de extremidade:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 e ele funciona. Mas, neste exemplo, o servidor usa um ponto de extremidade não padrão para hospedar os metadados. Portanto, Svcutil.exe deve ser instruído a usar a associação correta. Isso pode ser feito usando um arquivo de svcutil.  
  
 O arquivo de svcutil se parece com um arquivo de configuração do cliente normal. Os aspectos apenas incomuns são o nome do ponto de extremidade de cliente e o contrato:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 O nome do ponto de extremidade deve ser o nome do esquema do endereço no qual os metadados é hospedado e o contrato de ponto de extremidade deve ser `IMetadataExchange`. Portanto, quando Svcutil.exe é executado com uma linha de comando, como o seguinte:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ele procura por um ponto de extremidade chamado "http" e o contrato `IMetadataExchange` para configurar a associação e o comportamento da troca de comunicação com o ponto de extremidade de metadados. O restante do arquivo svcutil no exemplo especifica a configuração de associação e a credenciais de comportamento para corresponder à configuração do servidor do ponto de extremidade de metadados.  
  
 Para Svcutil.exe escolher a configuração de svcutil, Svcutil.exe deve ser no mesmo diretório que o arquivo de configuração. Como resultado, você deve copiar Svcutil.exe de seu local de instalação para o diretório que contém o arquivo de svcutil. Em seguida, do diretório, execute o seguinte comando:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 O entrelinhamento ". \\"garante que a cópia do Svcutil.exe neste diretório (aquele que tem um svcutil correspondente) é executada.  
  
## <a name="metadataresolver-client"></a>Cliente MetadataResolver  
 Se o cliente sabe o contrato e como se comunicar com os metadados em tempo de design, o cliente dinamicamente descobrir a associação e o endereço dos pontos de extremidade do aplicativo usando o `MetadataResolver`. Esse cliente de exemplo demonstra isso, mostrando como configurar a associação e as credenciais usadas pelo `MetadataResolver` criando e configurando um `MetadataExchangeClient`.  
  
 As mesmas informações de associação e o certificado apareceram no svcutil podem ser especificadas no modo imperativo o `MetadataExchangeClient`:  
  
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
  
 Com o `mexClient` configurado, podemos pode enumerar os contratos que estamos interessados em e usar `MetadataResolver` para buscar uma lista de pontos de extremidade com esses contratos:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Por fim, podemos usar as informações a partir desses pontos de extremidade para inicializar a associação e o endereço de um `ChannelFactory` usado para criar canais para se comunicar com os pontos de extremidade do aplicativo.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 O ponto principal do cliente neste exemplo é demonstrar que, se você estiver usando `MetadataResolver`e você deve especificar ligações personalizadas ou comportamentos para a comunicação de troca de metadados, você pode usar um `MetadataExchangeClient` para especificar essas configurações personalizadas.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e compilar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo na mesma máquina  
  
1. Execute Setup. bat da pasta de instalação de exemplo. Essa opção instala todos os certificados necessários para executar o exemplo. Observe que o Setup. bat usa a ferramenta de FindPrivateKey.exe, que está instalada executando setupCertTool.bat partir [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Execute o aplicativo cliente de \MetadataResolverClient\bin ou \SvcutilClient\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
3. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Remova os certificados com a execução CleanUp quando você terminar com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
#### <a name="to-run-the-sample-across-machines"></a>Para executar o exemplo entre máquinas  
  
1. No servidor, execute `setup.bat service`. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
2. No servidor, edite o Web. config para refletir o novo nome do certificado. Ou seja, alterar o `findValue` de atributo em de [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elemento para o nome de domínio totalmente qualificado da máquina.  
  
3. Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
4. No cliente, execute `setup.bat client`. Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado Client.com e exporta o certificado de cliente para um arquivo chamado da CER.  
  
5. No arquivo App. config do `MetadataResolverClient` no computador cliente, altere o valor do endereço do ponto de extremidade mex para coincidir com o novo endereço do seu serviço. Você pode fazer isso substituindo o localhost com o nome de domínio totalmente qualificado do servidor. Altere também a ocorrência de "localhost" no arquivo metadataResolverClient.cs para o novo nome de certificado de serviço (o nome de domínio totalmente qualificado do servidor). Fazer a mesma coisa para o App. config do projeto SvcutilClient.  
  
6. Copie o arquivo de Client. cer do diretório do cliente para o diretório de serviço no servidor.  
  
7. No cliente, execute `ImportServiceCert.bat`. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.  
  
8. No servidor, execute `ImportClientCert.bat`, isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.  
  
9. No computador do serviço, compile o projeto de serviço no Visual Studio e selecione a página de Ajuda em um navegador da web para verificar se ele está em execução.  
  
10. O computador cliente, execute o MetadataResolverClient ou o SvcutilClient do VS.  
  
    1.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
