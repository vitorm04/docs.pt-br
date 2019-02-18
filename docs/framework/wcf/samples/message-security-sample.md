---
title: Exemplo de segurança de mensagem
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 7e175be732f393382508a28f8a013e58db406a6f
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332358"
---
# <a name="message-security-sample"></a>Exemplo de segurança de mensagem
Este exemplo demonstra como implementar um aplicativo que usa o `basicHttpBinding` e segurança de mensagem. Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O modo de segurança de `basicHttpBinding` podem ser definidas com os seguintes valores: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` e `None`. No App. config arquivo seguinte serviço de exemplo, a definição de ponto de extremidade Especifica o `basicHttpBinding` e faz referência a uma configuração de ligação nomeada `Binding1`, conforme mostrado no seguinte exemplo de configuração:  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 Os conjuntos de configuração de associação a `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) para `Message` e define o `clientCredentialType` atributo do [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)para `Certificate` conforme mostrado no seguinte exemplo de configuração:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 O certificado que o serviço usa para se autenticar para o cliente é definido na seção behaviors do arquivo de configuração sob o `serviceCredentials` elemento. O modo de validação que se aplica ao certificado que o cliente usa para autenticar-se com o serviço também é definido na seção de comportamentos no `clientCertificate` elemento.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Os mesmos detalhes de associação e segurança são especificados no arquivo de configuração do cliente.  
  
 A identidade do chamador é exibida na janela do console de serviço, usando o código a seguir:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Para configurar e compilar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo na mesma máquina  
  
1.  Execute Setup. bat da pasta de instalação de exemplo. Essa opção instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Prompt de comando do SDK do Windows. Ele requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definido automaticamente dentro de um Prompt de comando do SDK do Windows.  
  
2.  Execute o aplicativo de serviço do \service\bin.  
  
3.  Execute o aplicativo de cliente do \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5.  Remova os certificados com a execução CleanUp quando você terminar com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
### <a name="to-run-the-sample-across-machines"></a>Para executar o exemplo entre máquinas  
  
1.  Crie um diretório na máquina do serviço para os binários de serviço.  
  
2.  Copie os arquivos de programa de serviço para o diretório de serviço no servidor. Também copie os arquivos Setup. bat, CleanUp e ImportClientCert.bat para o servidor.  
  
3.  Crie um diretório no computador cliente para os binários do cliente.  
  
4.  Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente. Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.  
  
5.  No servidor, execute `setup.bat service`. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6.  Editar Service.exe.config para refletir o novo nome do certificado (na `findValue` de atributo na [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemento) que é o mesmo que o nome de domínio totalmente qualificado da máquina. Também altere o valor do endereço base para especificar um nome de máquina totalmente qualificado em vez do localhost`.`  
  
7.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8.  No cliente, execute `setup.bat client`. Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado da CER.  
  
9. No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço. Você pode fazer isso substituindo o localhost com o nome de domínio totalmente qualificado do servidor. Também alterar o `findValue` atributo o [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) para o novo nome de certificado de serviço que é o nome de domínio totalmente qualificado do servidor.  
  
10. Copie o arquivo de Client. cer do diretório do cliente para o diretório de serviço no servidor.  
  
11. No cliente, execute ImportServiceCert.bat. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.  
  
12. No servidor, execute ImportClientCert.bat, isso importa o certificado do cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.  
  
13. No computador do serviço, execute Service.exe em um prompt de comando.  
  
14. No computador cliente, inicie Client.exe em uma janela do prompt de comando.  
  
    1.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a>Consulte também
