---
title: Exemplo de segurança de mensagem
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 43e1a9104bdd44509d86bd198559c5e7477a9964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183524"
---
# <a name="message-security-sample"></a>Exemplo de segurança de mensagem
Esta amostra demonstra como implementar um `basicHttpBinding` aplicativo que usa a segurança e a mensagem. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O modo `basicHttpBinding` de segurança pode ser `Message`definido `Transport` `TransportWithMessageCredential`para `TransportCredentialOnly` `None`os seguintes valores: , , e . No seguinte arquivo de serviço de amostra App.config, a definição de ponto final especifica e faz referência a `basicHttpBinding` uma configuração de vinculação nomeada, `Binding1`conforme mostrado na seguinte configuração de amostra:  
  
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
  
 A configuração `mode` de vinculação define `Message` o `clientCredentialType` atributo do [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) de segurança e define o atributo da [ \<mensagem>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) como `Certificate` mostrado na seguinte configuração de amostra:  
  
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
  
 O certificado que o serviço usa para autenticar-se ao cliente é definido `serviceCredentials` na seção de comportamentos do arquivo de configuração o elemento. O modo de validação que se aplica ao certificado que o cliente usa para autenticar-se ao serviço também é definido na seção de comportamentos o `clientCertificate` elemento.  
  
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
  
 Os mesmos detalhes de vinculação e segurança são especificados no arquivo de configuração do cliente.  
  
 A identidade do chamador é exibida na janela do console de serviço usando o seguinte código:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Para configurar e construir a amostra  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar a amostra na mesma máquina  
  
1. Executar Setup.bat da pasta de instalação de amostra. Isso instala todos os certificados necessários para a execução da amostra.  
  
    > [!NOTE]
    > O arquivo de lote Setup.bat foi projetado para ser executado a partir de um prompt de comando do Windows SDK. Requer que a variável ambiente MSSDK aponte para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente dentro de um prompt de comando Do Windows SDK.  
  
2. Execute o aplicativo de serviço a partir de \service\bin.  
  
3. Execute o aplicativo cliente a partir de \client\bin. A atividade do cliente é exibida no aplicativo do console cliente.  
  
4. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Remova os certificados executando Cleanup.bat quando terminar com a amostra. Outras amostras de segurança usam os mesmos certificados.  
  
### <a name="to-run-the-sample-across-machines"></a>Para executar a amostra através de máquinas  
  
1. Crie um diretório na máquina de serviço para os binários de serviço.  
  
2. Copie os arquivos do programa de serviço para o diretório de serviço no servidor. Copie também os arquivos Setup.bat, Cleanup.bat e ImportClientCert.bat para o servidor.  
  
3. Crie um diretório na máquina cliente para os binários do cliente.  
  
4. Copie os arquivos do programa cliente para o diretório do cliente na máquina cliente. Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.  
  
5. No servidor, `setup.bat service`execute. A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado da máquina e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6. Editar Service.exe.config para refletir o novo `findValue` nome do certificado (no atributo no [ \<elemento serviceCertificate>)](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) que é o mesmo que o nome de domínio totalmente qualificado da máquina. Também altere o valor do endereço base para especificar um nome de máquina totalmente qualificado em vez de localhost`.`  
  
7. Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente na máquina cliente.  
  
8. No cliente, `setup.bat client`corra. A `setup.bat` execução com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado do cliente para um arquivo chamado Client.cer.  
  
9. No arquivo Client.exe.config na máquina cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço. Você faz isso substituindo o localhost pelo nome de domínio totalmente qualificado do servidor. Também altere o atributo `findValue` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) do>de certificado padrão para o novo nome do certificado de serviço, que é o nome de domínio totalmente qualificado do servidor.  
  
10. Copie o arquivo Client.cer do diretório do cliente para o diretório de serviço situado no servidor.  
  
11. No cliente, execute ImportServiceCert.bat. Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.  
  
12. No servidor, execute ImportClientCert.bat, Isso importa o certificado do cliente do arquivo Client.cer para a loja LocalMachine - TrustedPeople.  
  
13. Na máquina de serviço, execute Service.exe a partir de um prompt de comando.  
  
14. Na máquina cliente, inicie client.exe a partir de uma janela de solicitação de comando.  
  
    1. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
- Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.  
  
    > [!NOTE]
    > Este script não remove certificados de serviço em um cliente ao executar esta amostra em máquinas. Se você tiver executado amostras de Windows Communication Foundation (WCF) que usam certificados em máquinas, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople. Para fazer isso, use `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` o seguinte comando: Por exemplo:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
