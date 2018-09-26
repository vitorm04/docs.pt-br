---
title: Message Security User Name
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
author: BrucePerlerMS
ms.openlocfilehash: 904916424c3ab199afd09a804c47b57a82e14158
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204304"
---
# <a name="message-security-user-name"></a>Message Security User Name
Este exemplo demonstra como implementar um aplicativo que usa WS-Security com autenticação de nome de usuário para o cliente e requer autenticação de servidor usando o certificado X.509v3 do servidor. Todas as mensagens de aplicativo entre o cliente e servidor assinadas e criptografadas. Por padrão, o nome de usuário e senha fornecidos pelo cliente são usados para fazer logon em uma conta válida do Windows. Este exemplo se baseia a [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). Esse exemplo consiste em um programa de console de cliente (Client.exe) e uma biblioteca de serviço (Service.dll) hospedado pelo Internet Information Services (IIS). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo também demonstra:  
  
-   O mapeamento padrão para as contas do Windows para que possa ser executada autorização adicional.  
  
-   Como acessar informações de identidade do chamador do código de serviço.  
  
 O serviço expõe um ponto de extremidade para se comunicar com o serviço, que é definido usando o arquivo de configuração Web. config. O ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com um padrão [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), cujo padrão é usando a segurança de mensagem. Este exemplo define o padrão [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) para usar a autenticação de nome de usuário do cliente. O comportamento Especifica que as credenciais do usuário devem ser usados para autenticação de serviço. O certificado do servidor deve conter o mesmo valor para o nome da entidade como o `findValue` de atributo em de [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
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
  
 A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato. A associação de cliente é configurado com os devidos `securityMode` e `authenticationMode`. Quando em execução em um cenário entre computadores, o endereço do ponto de extremidade de serviço deve ser alterado adequadamente.  
  
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
  
 A implementação do cliente define o nome de usuário e senha a ser usada.  

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

 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 O arquivo em lotes de Setup. bat incluído com os exemplos de MessageSecurity permite que você configure o servidor com um certificado apropriado para executar um aplicativo hospedado que exige a segurança baseada em certificado. O arquivo em lotes pode ser executado em dois modos. Para executar o arquivo em lote no modo único computador, digite `setup.bat` na linha de comando. Para executá-lo no tipo de modo de serviço `setup.bat service`. Você usa este modo, ao executar a amostra entre computadores. Consulte o procedimento de instalação no final deste tópico para obter detalhes.  
  
 O exemplo a seguir fornece uma visão geral sobre as diferentes seções dos arquivos de lote.  
  
-   Criando o certificado do servidor  
  
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
  
     A variável % SERVER_NAME % Especifica o nome do servidor. O certificado é armazenado no repositório de LocalMachine. Se o arquivo em lotes de Setup. bat é executado com um argumento de serviço (como `setup.bat service`) % % SERVER_NAME contém o nome de domínio totalmente qualificado do computador.  Caso contrário, o padrão é localhost.  
  
-   Instalando o certificado do servidor no repositório de certificados confiáveis do cliente  
  
     A linha a seguir copia o certificado do servidor para o repositório de pessoas confiáveis do cliente. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Concedendo permissões de chave privada do certificado  
  
     As seguintes linhas no arquivo em lotes bat Verifique o certificado de servidor armazenado no repositório de LocalMachine acessível para o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] conta de processo de trabalho.  
  
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
    >  Se você estiver usando um fora dos EUA Edição em inglês do Windows, você deve editar o arquivo Setup. bat e substitua o `NT AUTHORITY\NETWORK SERVICE` nome da conta com seu equivalente regional.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Certifique-se de que o caminho inclui a pasta onde Makecert.exe e FindPrivateKey.exe estão localizados.  
  
2.  Execute Setup. bat da pasta de instalação de exemplo em um prompt de comando do Visual Studio aberto com privilégios de administrador. Essa opção instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes de Setup. bat foi projetado para ser executado em um Prompt de comando Visual Studio. Ele requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definido automaticamente dentro de um Prompt de comando Visual Studio.  
  
3.  Verificar o acesso ao serviço usando um navegador, inserindo o endereço http://localhost/servicemodelsamples/service.svc.  
  
4.  Inicie o Client.exe no \client\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
5.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Crie um diretório no computador do serviço. Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet.  
  
2.  Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço. Certifique-se de que você copiar os arquivos no subdiretório \bin. Também copie os arquivos Setup. bat e Cleanup para o computador do serviço.  
  
3.  Crie um diretório no computador cliente para os binários do cliente.  
  
4.  Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente. Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.  
  
5.  No servidor, execute `setup.bat service` em um prompt de comando do Visual Studio aberta com privilégios de administrador. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6.  Editar o Web. config para refletir o novo nome de certificado (no atributo findValue no elemento serviceCertificate) que é o mesmo que o nome de domínio totalmente qualificado do computador`.`  
  
7.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8.  No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.  
  
9. No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.  
  
10. No computador cliente, inicie Client.exe em um prompt de comando. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Consulte também
