---
title: Message Security User Name
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183508"
---
# <a name="message-security-user-name"></a>Message Security User Name
Esta amostra demonstra como implementar um aplicativo que usa o WS-Security com autenticação de nome de usuário para o cliente e requer autenticação do servidor usando o certificado X.509v3 do servidor. Todas as mensagens de aplicativo entre o cliente e o servidor são assinadas e criptografadas. Por padrão, o nome de usuário e a senha fornecidos pelo cliente são usados para fazer logon em uma conta válida do Windows. Esta amostra é baseada no [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). Esta amostra consiste em um programa de console cliente (Client.exe) e uma biblioteca de serviços (Service.dll) hospedada pelo Internet Information Services (IIS). O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Esta amostra também demonstra:  
  
- O mapeamento padrão para contas do Windows para que a autorização adicional possa ser realizada.  
  
- Como acessar as informações de identidade do chamador a partir do código de serviço.  
  
 O serviço expõe um único ponto final para se comunicar com o serviço, que é definido usando o arquivo de configuração Web.config. O ponto final consiste em um endereço, um vinculativo e um contrato. A vinculação é configurada com um>padrão [ \<wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), que é padrão para usar a segurança de mensagem. Esta amostra define o padrão [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) para usar a autenticação do nome de usuário do cliente. O comportamento especifica que as credenciais do usuário devem ser usadas para autenticação de serviço. O certificado de servidor deve conter o `findValue` mesmo valor para o nome do objeto que o atributo no [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 A configuração de ponto final do cliente consiste em um endereço absoluto para o ponto final do serviço, a vinculação e o contrato. A vinculação do cliente `securityMode` é `authenticationMode`configurada com o apropriado e . Ao ser executado em um cenário de computador entre computadores, o endereço de ponto final de serviço deve ser alterado em conformidade.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 A implementação do cliente define o nome de usuário e a senha a serem usados.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 O arquivo de lote Setup.bat incluído com as amostras MessageSecurity permite configurar o servidor com um certificado relevante para executar um aplicativo hospedado que requer segurança baseada em certificados. O arquivo em lote pode ser executado em dois modos. Para executar o arquivo em lote no `setup.bat` modo de computador único, digite na linha de comando. Para executá-lo `setup.bat service`no tipo de modo de serviço . Você usa este modo ao executar a amostra em computadores. Consulte o procedimento de configuração no final deste tópico para obter detalhes.  
  
 O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote.  
  
- Criando o certificado do servidor  
  
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
  
     A variável %SERVER_NAME% especifica o nome do servidor. O certificado é armazenado na loja LocalMachine. Se o arquivo de lote Setup.bat for executado `setup.bat service`com um argumento de serviço (como ) o %SERVER_NAME% contém o nome de domínio totalmente qualificado do computador.  Caso contrário, ele é padrão para host local.  
  
- Instalando o certificado do servidor na loja de certificados confiáveis do cliente  
  
     A linha a seguir copia o certificado do servidor na loja de pessoas confiáveis do cliente. Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente. Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Concessão de permissões na chave privada do certificado  
  
     As seguintes linhas no arquivo setup.bat batch tornam o certificado de servidor armazenado na loja LocalMachine acessível à conta do processo do trabalhador ASP.NET.  
  
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
    > Se você estiver usando uma edição não-americana em inglês do Windows, você `NT AUTHORITY\NETWORK SERVICE` deve editar o arquivo Setup.bat e substituir o nome da conta pelo seu equivalente regional.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar a amostra no mesmo computador  
  
1. Certifique-se de que o caminho inclui a pasta onde o Makecert.exe e o FindPrivateKey.exe estão localizados.  
  
2. Executar setup.bat da pasta de instalação de amostra em um Prompt de comando do desenvolvedor para o Visual Studio aberto com privilégios de administrador. Isso instala todos os certificados necessários para a execução da amostra.  
  
    > [!NOTE]
    > O arquivo de lote Setup.bat foi projetado para ser executado a partir de um prompt de comando do desenvolvedor para o Visual Studio. Requer que a variável ambiente de caminho aponte para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente dentro de um Prompt de comando do desenvolvedor para o Visual Studio.  
  
3. Verifique o acesso ao serviço usando `http://localhost/servicemodelsamples/service.svc`um navegador inserindo o endereço .
  
4. Inicie client.exe a partir de \client\bin. A atividade do cliente é exibida no aplicativo do console cliente.  
  
5. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar a amostra através de computadores  
  
1. Crie um diretório no computador de serviço. Crie um aplicativo virtual chamado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de Serviços de Informação da Internet.  
  
2. Copie os arquivos do programa de serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço. Certifique-se de copiar os arquivos no subdiretório \bin. Copie também os arquivos Setup.bat e Cleanup.bat para o computador de serviço.  
  
3. Crie um diretório no computador cliente para os binários do cliente.  
  
4. Copie os arquivos do programa cliente para o diretório do cliente no computador cliente. Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.  
  
5. No servidor, `setup.bat service` execute em um Prompt de comando de desenvolvedor para o Visual Studio aberto com privilégios de administrador. A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6. Editar Web.config para refletir o novo nome do certificado (no atributo findValue no elemento serviceCertificate) que é o mesmo que o nome de domínio totalmente qualificado do computador`.`  
  
7. Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8. No arquivo Client.exe.config no computador do cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço.  
  
9. No cliente, execute ImportServiceCert.bat em um Prompt de comando de desenvolvedor para o Visual Studio aberto com privilégios de administrador. Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.  
  
10. No computador do cliente, inicie client.exe a partir de um prompt de comando. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
- Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.  
  
    > [!NOTE]
    > Este script não remove certificados de serviço em um cliente ao executar essa amostra em computadores. Se você tiver executado amostras de WCF (Windows Communication Foundation, fundação de comunicação do Windows) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople. Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` seguinte comando: Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
