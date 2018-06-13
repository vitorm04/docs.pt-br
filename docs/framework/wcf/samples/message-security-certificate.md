---
title: Certificado de mensagem de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 769827d10139a659971890a452227b650e89ba20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508431"
---
# <a name="message-security-certificate"></a>Certificado de mensagem de segurança
Este exemplo demonstra como implementar um aplicativo que usa o WS-Security com autenticação de certificado x. 509 v3 para o cliente e requer a autenticação de servidor usando o certificado do servidor x. 509 v3. Este exemplo usa as configurações padrão, de modo que todas as mensagens de aplicativo entre o cliente e servidor assinadas e criptografadas. Este exemplo se baseia o [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) e consiste em um programa de console de cliente e uma biblioteca de serviços hospedados pelo Internet Information Services (IIS). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O exemplo demonstra o controle de autenticação usando configuração e como obter a identidade do chamador do contexto de segurança, como mostrado no código de exemplo a seguir.  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 O serviço expõe um ponto de extremidade para se comunicar com o serviço e um ponto de extremidade para expor o documento WSDL do serviço usando o protocolo WS-MetadataExchange, definido usando o arquivo de configuração (Web. config). O ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com um padrão [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento, que foi padronizado para usar segurança de mensagem. Este exemplo define o `clientCredentialType` de atributo para o certificado para exigir autenticação de cliente.  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 O comportamento Especifica as credenciais do serviço que são usadas quando o cliente autentica o serviço. O nome de assunto do certificado de servidor é especificado no `findValue` atributo o [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) elemento.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato. A ligação do cliente é configurado com o modo de segurança apropriadas e modo de autenticação. Quando em execução em um cenário entre computadores, certifique-se de que o endereço do ponto de extremidade de serviço é alterado.  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 A implementação do cliente pode definir o certificado a ser usado, por meio do arquivo de configuração ou código. O exemplo a seguir mostra como definir o certificado a ser usado no arquivo de configuração.  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 O exemplo a seguir mostra como chamar o serviço em seu programa.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Arquivo em lotes bat incluído com os exemplos de segurança de mensagem permite que você configure o cliente e o servidor com certificados relevantes para executar um aplicativo hospedado que exige a segurança baseada em certificado. O arquivo em lotes pode ser executado em três modos. Para ser executado no tipo de computador único modo **bat** em um Prompt de comando Visual Studio; para o tipo de modo de serviço **bat serviço**; e para o tipo de modo de cliente **bat cliente** . Use o modo de cliente e servidor ao executar a amostra entre computadores. Consulte o procedimento de instalação no final deste tópico para obter detalhes. O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada:  
  
-   Criando o certificado de cliente.  
  
     A seguinte linha no arquivo de lote cria o certificado de cliente. O nome do cliente especificado é usado no nome da entidade do certificado criado. O certificado é armazenado no `My` armazenar no `CurrentUser` local do repositório.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado de cliente no repositório de certificados confiáveis do servidor.  
  
     A seguinte linha nas cópias do arquivo em lotes o certificado cliente TrustedPeople do servidor armazenar para que o servidor possa fazer a confiança relevante ou decisões não confiáveis. Em ordem para um certificado instalado no repositório de TrustedPeople para ser confiável por um serviço do Windows Communication Foundation (WCF), o modo de validação de certificado de cliente deve ser definido como `PeerOrChainTrust` ou `PeerTrust`. Consulte o exemplo de configuração de serviço anterior para saber como isso pode ser feito usando um arquivo de configuração.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
-   Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     A variável % SERVER_NAME % Especifica o nome do servidor. O certificado é armazenado no repositório de LocalMachine. Se o arquivo em lotes bat é executado com um argumento de serviço (como **bat serviço**) % SERVER_NAME % contém o nome de domínio totalmente qualificado do computador. Caso contrário, o padrão é localhost.  
  
-   Instalando o certificado de servidor no repositório de certificados confiáveis do cliente.  
  
     A linha a seguir copia o certificado do servidor para o armazenamento de pessoas confiáveis do cliente. Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Concedendo permissões de chave privada do certificado.  
  
     As seguintes linhas no arquivo bat Verifique o certificado de servidor armazenado no repositório de LocalMachine acessível para o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] conta de processo do operador.  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  Se você estiver usando um fora dos EUA Edição em inglês do Windows, você deve editar o BAT arquivo e substitua o nome da conta "NT AUTHORITY\NETWORK SERVICE" por seu equivalente regional.  
  
> [!NOTE]
>  As ferramentas usadas nesse arquivo em lotes estão localizadas em C:\Program Files\Microsoft Visual Studio 8 \ Common7\Tools ou C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. Um desses diretórios deve estar no caminho do sistema. Se você tiver instalado o Visual Studio, a maneira mais fácil de obter esse diretório no caminho é abrir o Prompt de comando do Visual Studio. Clique em **iniciar**e, em seguida, selecione **todos os programas**, **Visual Studio 2012**, **ferramentas**. Esse prompt de comando tem os caminhos apropriados já configurados. Caso contrário, você deve adicionar o diretório apropriado para seu caminho manualmente.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Abra um Prompt de comando do Visual Studio com privilégios de administrador e execute bat da pasta de instalação do exemplo. Isso instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes bat foi projetado para ser executado a partir de um Prompt de comando Visual Studio. Isso requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente dentro de um Visual Studio Command Prompt (2010).  
  
2.  Verifique se o acesso ao serviço usando um navegador inserindo o endereço `http://localhost/servicemodelsamples/service.svc`.  
  
3.  Inicie Client.exe de \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Crie um diretório no computador de serviço. Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet (IIS).  
  
2.  Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço. Certifique-se de que você copiar os arquivos no subdiretório \bin. Também copie os arquivos. bat, Cleanup.bat e ImportClientCert.bat para o computador do serviço.  
  
3.  Crie um diretório no computador cliente para os binários do cliente.  
  
4.  Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente. Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.  
  
5.  No servidor, execute **bat serviço** em um prompt de comando do Visual Studio com privilégios de administrador. Executando **bat** com o **service** argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6.  Editar o Web. config para refletir o novo nome de certificado (no `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador.  
  
7.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8.  No cliente, execute **bat cliente** em um prompt de comando do Visual Studio com privilégios de administrador. Executando **bat** com o **cliente** argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado cer.  
  
9. No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço. Faça isso substituindo localhost com o nome de domínio totalmente qualificado do servidor.  
  
10. Copie o arquivo CER do diretório do cliente para o diretório de serviço no servidor.  
  
11. No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio com privilégios administrativos. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.  
  
12. No servidor, execute ImportClientCert.bat em um prompt de comando do Visual Studio com privilégios administrativos. Isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.  
  
13. No computador cliente, inicie o Client.exe em uma janela de prompt de comando. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
-   Execute Cleanup.bat na pasta exemplos depois de terminar de executar o exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Consulte também
