---
title: Tokens com suporte
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 5f2b1500f54f8ade3c4924e3eb22cd022c6800c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976645"
---
# <a name="supporting-tokens"></a>Tokens com suporte
O que dão suporte a Tokens que demonstra como adicionar tokens adicionais a uma mensagem que usa WS-Security. O exemplo adiciona um token de segurança binário X.509, além de um token de segurança do nome de usuário. O token é passado em um cabeçalho de mensagem do WS-Security do cliente para o serviço e parte da mensagem é assinado com a chave privada associada ao token de segurança x. 509 para provar a posse do certificado X.509 para o receptor. Isso é útil no caso de quando há um requisito de ter várias declarações associadas com uma mensagem para autentica ou autoriza o remetente. O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.

## <a name="demonstrates"></a>Demonstra
 O exemplo demonstra:

-   Como um cliente pode passar tokens de segurança adicionais para um serviço.

-   Como o servidor possa acessar declarações associadas com tokens de segurança adicionais.

-   Como o certificado X.509 do servidor é usado para proteger a chave simétrica usada para assinatura e criptografia de mensagem.

> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Cliente autentica com o Token de nome de usuário e dar suporte a Token de segurança X.509
 O serviço expõe um ponto de extremidade para se comunicar por meio de programação criado usando o `BindingHelper` e `EchoServiceHost` classes. O ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com uma ligação personalizada usando `SymmetricSecurityBindingElement` e `HttpTransportBindingElement`. Este exemplo define o `SymmetricSecurityBindingElement` usar um certificado de serviço x. 509 para proteger a chave simétrica durante a transmissão e passar uma `UserNameToken` juntamente com o suporte a `X509SecurityToken` em um cabeçalho de mensagem do WS-Security. A chave simétrica é usada para criptografar o corpo da mensagem e o token de segurança do nome de usuário. O token de suporte é passado como um token de segurança binário adicional no cabeçalho da mensagem do WS-Security. A autenticidade do token de suporte foi comprovada por parte da mensagem de assinatura com a chave privada associada com a segurança X.509 suporte token.

```csharp
public static Binding CreateMultiFactorAuthenticationBinding()
{
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

    // the message security binding element will be configured to require 2 tokens:
    // 1) A username-password encrypted with the service token
    // 2) A client certificate used to sign the message

    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();

    // Create supporting token parameters for the client X509 certificate.
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();
    // Specify that the supporting token is passed in message send by the client to the service
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;
    // Turn off derived keys
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);

    // Create a CustomBinding based on the constructed security binding element.
    return new CustomBinding(messageSecurity, httpTransport);
}
```

 O comportamento Especifica as credenciais de serviço que devem ser usados para autenticação de cliente e também informações sobre o certificado X.509 de serviço. O exemplo usa `CN=localhost` como um nome de assunto no certificado X.509 de serviço.

```csharp
override protected void InitializeRuntime()
{
    // Extract the ServiceCredentials behavior or create one.
    ServiceCredentials serviceCredentials =
        this.Description.Behaviors.Find<ServiceCredentials>();
    if (serviceCredentials == null)
    {
        serviceCredentials = new ServiceCredentials();
        this.Description.Behaviors.Add(serviceCredentials);
    }

    // Set the service certificate
    serviceCredentials.ServiceCertificate.SetCertificate(
                                       "CN=localhost");

/*
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.
*/
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;

    // Create the custom binding and add an endpoint to the service.
    Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
    this.AddServiceEndpoint(typeof(IEchoService),
                          multipleTokensBinding, string.Empty);
    base.InitializeRuntime();
}
```

 Código de serviço:

```csharp
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]
public class EchoService : IEchoService
{
    public string Echo()
    {
        string userName;
        string certificateSubjectName;
        GetCallerIdentities(
            OperationContext.Current.ServiceSecurityContext,
            out userName,
            out certificateSubjectName);
            return $"Hello {userName}, {certificateSubjectName}";
    }

    public void Dispose()
    {
    }

    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,
            string claimType, out TClaimResource resourceValue)
            where TClaimResource : class
    {
        resourceValue = default(TClaimResource);
        IEnumerable<Claim> matchingClaims =
            claimSet.FindClaims(claimType, Rights.PossessProperty);
        if(matchingClaims == null)
            return false;
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
        if (enumerator.MoveNext())
        {
            resourceValue =
              (enumerator.Current.Resource == null) ? null :
              (enumerator.Current.Resource as TClaimResource);
            return true;
        }
        else
        {
            return false;
        }
    }

    // Returns the username and certificate subject name provided by
    //the client
    void GetCallerIdentities(ServiceSecurityContext
        callerSecurityContext,
        out string userName, out string certificateSubjectName)
    {
        userName = null;
        certificateSubjectName = null;

       // Look in all the claimsets in the authorization context
       foreach (ClaimSet claimSet in
               callerSecurityContext.AuthorizationContext.ClaimSets)
       {
            if (claimSet is WindowsClaimSet)
            {
                // Try to find a Name claim. This will have been
                // generated from the windows username.
                string tmpName;
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                      out tmpName))
                {
                    userName = tmpName;
                }
            }
            else if (claimSet is X509CertificateClaimSet)
            {
                // Try to find an X500DisinguishedName claim. This will
                // have been generated from the client certificate.
                X500DistinguishedName tmpDistinguishedName;
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,
                               ClaimTypes.X500DistinguishedName,
                               out tmpDistinguishedName))
                {
                    certificateSubjectName = tmpDistinguishedName.Name;
                }
            }
        }
    }
}
```

 O ponto de extremidade do cliente é configurado de forma semelhante ao ponto de extremidade de serviço. O cliente usa o mesmo `BindingHelper` classe para criar uma associação. O restante da instalação está localizado em `Client` classe. O cliente define informações sobre o token de segurança de nome de usuário, o token de segurança X.509 suporte e informações sobre o certificado X.509 de serviço no código do programa de instalação para a coleção de comportamentos de ponto de extremidade do cliente.

```csharp
 static void Main()
 {
     // Create the custom binding and an endpoint address for
     // the service.
     Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
         EndpointAddress serviceAddress = new EndpointAddress(
         "http://localhost/servicemodelsamples/service.svc");
       ChannelFactory<IEchoService> channelFactory = null;
       IEchoService client = null;

       Console.WriteLine("Username authentication required.");
       Console.WriteLine(
         "Provide a valid machine or domain account. [domain\\user]");
       Console.WriteLine("   Enter username:");
       string username = Console.ReadLine();
       Console.WriteLine("   Enter password:");
       string password = "";
       ConsoleKeyInfo info = Console.ReadKey(true);
       while (info.Key != ConsoleKey.Enter)
       {
           if (info.Key != ConsoleKey.Backspace)
           {
               if (info.KeyChar != '\0')
               {
                   password += info.KeyChar;
                }
                info = Console.ReadKey(true);
            }
            else if (info.Key == ConsoleKey.Backspace)
            {
                if (password != "")
                {
                    password =
                       password.Substring(0, password.Length - 1);
                }
                info = Console.ReadKey(true);
            }
         }
         for (int i = 0; i < password.Length; i++)
            Console.Write("*");
         Console.WriteLine();
         try
         {
           // Create a proxy with the previously create binding and
           // endpoint address
              channelFactory =
                 new ChannelFactory<IEchoService>(
                     multipleTokensBinding, serviceAddress);
           // configure the username credentials, the client
           // certificate and the server certificate on the channel
           // factory
           channelFactory.Credentials.UserName.UserName = username;
           channelFactory.Credentials.UserName.Password = password;
           channelFactory.Credentials.ClientCertificate.SetCertificate(
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);
           client = channelFactory.CreateChannel();
           Console.WriteLine("Echo service returned: {0}",
                                           client.Echo());

           ((IChannel)client).Close();
           channelFactory.Close();
        }
        catch (CommunicationException e)
        {
         Abort((IChannel)client, channelFactory);
         // if there is a fault then print it out
         FaultException fe = null;
         Exception tmp = e;
         while (tmp != null)
         {
            fe = tmp as FaultException;
            if (fe != null)
            {
                break;
            }
            tmp = tmp.InnerException;
        }
        if (fe != null)
        {
           Console.WriteLine("The server sent back a fault: {0}",
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);
        }
        else
        {
         Console.WriteLine("The request failed with exception: {0}",e);
        }
    }
    catch (TimeoutException)
    {
        Abort((IChannel)client, channelFactory);
        Console.WriteLine("The request timed out");
    }
    catch (Exception e)
    {
         Abort((IChannel)client, channelFactory);
          Console.WriteLine(
          "The request failed with unexpected exception: {0}", e);
    }
    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();
}
```

## <a name="displaying-callers-information"></a>Exibindo informações de chamadores
 Para exibir informações do chamador, você pode usar o `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` conforme mostrado no código a seguir. O `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contém declarações de autorização associadas ao chamador atual. Essas declarações são fornecidas automaticamente pelo Windows Communication Foundation (WCF) para cada token recebido na mensagem.

```csharp
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string
                         claimType, out TClaimResource resourceValue)
    where TClaimResource : class
{
    resourceValue = default(TClaimResource);
    IEnumerable<Claim> matchingClaims =
    claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
          return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    if (enumerator.MoveNext())
    {
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);
        return true;
    }
    else
    {
         return false;
    }
}

// Returns the username and certificate subject name provided by the client
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)
{
    userName = null;
    certificateSubjectName = null;

    // Look in all the claimsets in the authorization context
    foreach (ClaimSet claimSet in
      callerSecurityContext.AuthorizationContext.ClaimSets)
    {
        if (claimSet is WindowsClaimSet)
        {
            // Try to find a Name claim. This will have been generated
            //from the windows username.
            string tmpName;
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                     out tmpName))
            {
                userName = tmpName;
            }
        }
        else if (claimSet is X509CertificateClaimSet)
         {
            //Try to find an X500DisinguishedName claim.
            //This will have been generated from the client
            //certificate.
            X500DistinguishedName tmpDistinguishedName;
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,
               ClaimTypes.X500DistinguishedName,
               out tmpDistinguishedName))
            {
                    certificateSubjectName = tmpDistinguishedName.Name;
            }
        }
    }
}
```

## <a name="running-the-sample"></a>A execução do exemplo
 Quando você executar o exemplo, o cliente primeiro solicita que você forneça o nome de usuário e senha para o token de nome de usuário. Certifique-se de fornecer valores corretos para sua conta do sistema, pois o WCF no serviço mapeia os valores fornecidos no token de nome de usuário para a identidade fornecida pelo sistema. Depois disso, o cliente exibe a resposta do serviço. Pressione ENTER na janela do cliente para desligar o cliente.

## <a name="setup-batch-file"></a>Arquivo de lote
 O arquivo em lotes de Setup. bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar o aplicativo de serviços de informações da Internet (IIS) hospedado que exige a segurança baseada em certificado do servidor. Esse arquivo em lotes deve ser modificado para funcionar em máquinas ou para trabalhar em um caso de não hospedados.

 O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.

### <a name="creating-the-client-certificate"></a>Criando o certificado do cliente
 As seguintes linhas do arquivo em lotes bat criam o certificado do cliente a ser usado. O `%CLIENT_NAME%` variável Especifica o assunto do certificado do cliente. Este exemplo usa "client.com" como o nome da entidade.

 O certificado é armazenado no repositório My (pessoal) sob o `CurrentUser` local do repositório.

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Instalação do certificado de cliente na Store de confiáveis do servidor
 A seguinte linha no arquivo em lotes bat copia o certificado do cliente para o armazenamento de pessoas confiáveis do servidor. Esta etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis do sistema do servidor. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a>Criando o certificado do servidor
 As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado. O `%SERVER_NAME%` variável Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. O padrão nesse arquivo em lotes é localhost.

 O certificado é armazenado no repositório My (pessoal) em um local de repositório LocalMachine. O certificado é armazenado no repositório de LocalMachine para os serviços hospedados no IIS. Para serviços de hospedagem interna, você deve modificar o arquivo em lotes para armazenar o certificado do servidor no local de repositório CurrentUser, substituindo a cadeia de caracteres LocalMachine por CurrentUser.

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Instalar o certificado do servidor em Store de certificado confiável do cliente
 As seguintes linhas na cópia de arquivo de lote o certificado do servidor Setup. bat as pessoas confiáveis do cliente ao repositório. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a>Habilitando o acesso à chave privada do certificado
 Para habilitar o acesso à chave privada do certificado do serviço hospedado no IIS, a conta de usuário sob a qual o processo hospedados no IIS está em execução deve ser concedida permissões apropriadas para a chave privada. Isso é realizado pelas últimas etapas no script de Setup. bat.

```
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Para executar o exemplo em uma configuração ou entre máquinas, use as instruções a seguir.

##### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo na mesma máquina

1. Execute Setup. bat da pasta de instalação de exemplo dentro de um prompt de comando do Visual Studio 2012 executado com privilégios de administrador. Essa opção instala todos os certificados necessários para executar o exemplo.

    > [!NOTE]
    >  O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2012 Prompt de comando. A variável de ambiente PATH definido dentro de pontos de Prompt de comando do Visual Studio 2012 para o diretório que contém executáveis exigido pelo script de Setup. bat. Certifique-se de remover os certificados com a execução CleanUp quando terminar com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
2. Inicie o Client.exe no \client\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
3. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-run-the-sample-across-machines"></a>Para executar o exemplo entre máquinas  
  
1. Crie um diretório no computador do serviço. Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet (IIS).  
  
2. Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual na máquina do serviço. Certifique-se de que você copiar os arquivos no subdiretório \bin. Também copie os arquivos Setup. bat, CleanUp e ImportClientCert.bat para o computador de serviço.  
  
3. Crie um diretório no computador cliente para os binários do cliente.  
  
4. Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente. Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.  
  
5. No servidor, execute `setup.bat service` em um Prompt de comando do desenvolvedor para Visual Studio é aberto com privilégios de administrador. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6. Editar o Web. config para refletir o novo nome do certificado (na `findValue` de atributo no [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é igual ao nome de domínio totalmente qualificado da máquina.  
  
7. Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8. No cliente, execute `setup.bat client` em um Prompt de comando do desenvolvedor para Visual Studio é aberto com privilégios de administrador. Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado da CER.  
  
9. No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço. Fazer isso, substitua localhost pelo nome de domínio totalmente qualificado do servidor.  
  
10. Copie o arquivo de Client. cer do diretório do cliente para o diretório de serviço no servidor.  
  
11. No cliente, execute ImportServiceCert.bat. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.  
  
12. No servidor, execute ImportClientCert.bat, isso importa o certificado do cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.  
  
13. No computador cliente, inicie Client.exe em uma janela do prompt de comando. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
> [!NOTE]
>  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas. Se você executou os exemplos do WCF que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
