---
title: Certificado de mensagem de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 92e656f36ae0af851def393575cbb7d418bc4a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183530"
---
# <a name="message-security-certificate"></a>Certificado de mensagem de segurança
Esta amostra demonstra como implementar um aplicativo que usa o WS-Security com autenticação de certificado X.509 v3 para o cliente e requer autenticação do servidor usando o certificado X.509 v3 do servidor. Essa amostra usa configurações padrão para que todas as mensagens de aplicativo entre o cliente e o servidor sejam assinadas e criptografadas. Esta amostra é baseada no [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) e consiste em um programa de console cliente e uma biblioteca de serviços hospedada pelo Internet Information Services (IIS). O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A amostra demonstra o controle da autenticação usando a configuração e como obter a identidade do chamador a partir do contexto de segurança, conforme mostrado no código de amostra a seguir.  

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
  
 O serviço expõe um ponto final para se comunicar com o serviço e um ponto final para expor o documento WSDL do serviço usando o protocolo WS-MetadataExchange, definido usando o arquivo de configuração (Web.config). O ponto final consiste em um endereço, um vinculativo e um contrato. A vinculação é configurada com um elemento padrão [ \<wsHttpBinding>,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) que é padrão para usar a segurança da mensagem. Esta amostra `clientCredentialType` define o atributo como Certificado para exigir a autenticação do cliente.  
  
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
  
 O comportamento especifica as credenciais do serviço que são usadas quando o cliente autentica o serviço. O nome do assunto do `findValue` certificado do servidor é especificado no atributo no [ \<elemento serviceCredentials>.](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
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
  
 A configuração de ponto final do cliente consiste em um endereço absoluto para o ponto final do serviço, a vinculação e o contrato. A vinculação do cliente é configurada com o modo de segurança e o modo de autenticação apropriados. Ao ser executado em um cenário de computador entre computadores, certifique-se de que o endereço de ponto final do serviço seja alterado de acordo.  
  
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
  
 A implementação do cliente pode definir o certificado para usar, seja através do arquivo de configuração ou através de código. A amostra a seguir mostra como definir o certificado para usar no arquivo de configuração.  
  
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
  
 A amostra a seguir mostra como chamar o serviço em seu programa.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 O arquivo de lote Setup.bat incluído nas amostras de segurança de mensagens permite configurar o cliente e o servidor com certificados relevantes para executar um aplicativo hospedado que requer segurança baseada em certificados. O arquivo em lote pode ser executado em três modos. Para executar em setup de tipo de modo de computador **único.bat** em um prompt de comando de desenvolvedor para o Visual Studio ; para o serviço de modo de serviço **setup.bat**service; e para configuração do tipo de modo **cliente.bat client**. Use o modo cliente e servidor ao executar a amostra em computadores. Consulte o procedimento de configuração no final deste tópico para obter detalhes. O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote para que eles possam ser modificados para serem executados na configuração apropriada:  
  
- Criando o certificado do cliente.  
  
     A linha a seguir no arquivo de lote cria o certificado do cliente. O nome do cliente especificado é usado no nome do assunto do certificado criado. O certificado é `My` armazenado `CurrentUser` na loja no local da loja.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- Instalando o certificado de cliente na loja de certificados confiáveis do servidor.  
  
     A linha a seguir no arquivo em lote copia o certificado do cliente na loja TrustedPeople do servidor para que o servidor possa tomar as decisões de confiança ou não confiáveis relevantes. Para que um certificado instalado na loja TrustedPeople seja confiável por um serviço wcf da Windows Communication `PeerOrChainTrust` `PeerTrust`Foundation (Windows Communication Foundation), o modo de validação do certificado do cliente deve ser configurado para ou . Consulte a amostra de configuração de serviço anterior para saber como isso pode ser feito usando um arquivo de configuração.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     A variável %SERVER_NAME% especifica o nome do servidor. O certificado é armazenado na loja LocalMachine. Se o arquivo de lote Setup.bat for executado com um argumento de serviço (como, **setup.bat service)** o %SERVER_NAME% contém o nome de domínio totalmente qualificado do computador. Caso contrário, ele é padrão para host local.  
  
- Instalando o certificado do servidor na loja de certificados confiáveis do cliente.  
  
     A linha a seguir copia o certificado do servidor na loja de pessoas confiáveis do cliente. Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente. Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Concedendo permissões na chave privada do certificado.  
  
     As seguintes linhas no arquivo Setup.bat tornam o certificado de servidor armazenado na loja LocalMachine acessível à conta do processo do ASP.NET trabalhador.  
  
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
    > Se você estiver usando uma edição não-americana do Windows, você deve editar o arquivo Setup.bat e substituir o nome da conta "NT AUTHORITY\NETWORK SERVICE" pelo seu equivalente regional.  
  
> [!NOTE]
> As ferramentas usadas neste arquivo em lote estão localizadas em c:\Program Files\Microsoft Visual Studio 8\Common7\\tools ou C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. Um desses diretórios deve estar no seu caminho do sistema. Se você tiver o Visual Studio instalado, a maneira mais fácil de obter este diretório em seu caminho é abrir o Prompt de Comando do Desenvolvedor para o Visual Studio. Clique **em Iniciar**e selecione Todos os **Programas,** Visual Studio **2012,** **Ferramentas.** Este prompt de comando tem os caminhos apropriados já configurados. Caso contrário, você deve adicionar o diretório apropriado ao seu caminho manualmente.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está no seguinte diretório:  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar a amostra no mesmo computador  
  
1. Abra um prompt de comando de desenvolvedor para o Visual Studio com privilégios de administrador e execute Setup.bat a partir da pasta de instalação de amostra. Isso instala todos os certificados necessários para a execução da amostra.  
  
    > [!NOTE]
    > O arquivo de lote Setup.bat foi projetado para ser executado a partir de um prompt de comando do desenvolvedor para o Visual Studio. Requer que a variável ambiente de caminho aponte para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente dentro de um Prompt de comando do desenvolvedor para o Visual Studio (2010).  
  
2. Verifique o acesso ao serviço usando `http://localhost/servicemodelsamples/service.svc`um navegador inserindo o endereço .  
  
3. Inicie client.exe a partir de \client\bin. A atividade do cliente é exibida no aplicativo do console cliente.  
  
4. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar a amostra através de computadores  
  
1. Crie um diretório no computador de serviço. Crie um aplicativo virtual chamado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de Serviços de Informação da Internet (IIS).  
  
2. Copie os arquivos do programa de serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço. Certifique-se de copiar os arquivos no subdiretório \bin. Copie também os arquivos Setup.bat, Cleanup.bat e ImportClientCert.bat para o computador de serviço.  
  
3. Crie um diretório no computador cliente para os binários do cliente.  
  
4. Copie os arquivos do programa cliente para o diretório do cliente no computador cliente. Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.  
  
5. No servidor, execute o **serviço setup.bat** em um Prompt de comando do desenvolvedor para o Visual Studio com privilégios de administrador. Executar **setup.bat** com o argumento **de serviço** cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6. Editar Web.config para refletir o novo `findValue` nome do certificado (no atributo no [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador.  
  
7. Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8. No cliente, execute o **cliente setup.bat** em um Prompt de comando do desenvolvedor para o Visual Studio com privilégios de administrador. Executar **setup.bat** com o argumento do **cliente** cria um certificado de cliente chamado client.com e exporta o certificado do cliente para um arquivo chamado Client.cer.  
  
9. No arquivo Client.exe.config no computador do cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço. Faça isso substituindo o localhost pelo nome de domínio totalmente qualificado do servidor.  
  
10. Copie o arquivo Client.cer do diretório do cliente para o diretório de serviço situado no servidor.  
  
11. No cliente, execute ImportServiceCert.bat em um Prompt de comando de desenvolvedor para o Visual Studio com privilégios administrativos. Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.  
  
12. No servidor, execute ImportClientCert.bat em um Prompt de comando de desenvolvedor para o Visual Studio com privilégios administrativos. Isso importa o certificado do cliente do arquivo Client.cer para a loja LocalMachine - TrustedPeople.  
  
13. No computador do cliente, inicie client.exe a partir de uma janela de solicitação de comando. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
- Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.  
  
    > [!NOTE]
    > Este script não remove certificados de serviço em um cliente ao executar essa amostra em computadores. Se você tiver executado amostras de WCF (Windows Communication Foundation, fundação de comunicação do Windows) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople. Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` seguinte comando: Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
