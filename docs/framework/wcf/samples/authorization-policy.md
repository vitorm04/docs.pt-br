---
title: Política de autorização
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 36ec1029c8fed57957eb463808de442e74abdf9c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463944"
---
# <a name="authorization-policy"></a>Política de autorização

Esta amostra demonstra como implementar uma política de autorização de sinistro personalizado e um gerente de autorização de serviço personalizado associado. Isso é útil quando o serviço faz verificações de acesso baseadas em sinistros às operações de serviço e antes das verificações de acesso, concede ao chamador certos direitos. Esta amostra mostra tanto o processo de adição de sinistros quanto o processo para fazer uma verificação de acesso em relação ao conjunto de sinistros finalizado. Todas as mensagens de aplicativo entre o cliente e o servidor são assinadas e criptografadas. Por padrão, `wsHttpBinding` com a vinculação, um nome de usuário e senha fornecidos pelo cliente são usados para fazer logon em uma conta válida do Windows NT. Esta amostra demonstra como <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> utilizar um costume para autenticar o cliente. Além disso, esta amostra mostra o cliente autenticando-se ao serviço usando um certificado X.509. Esta amostra mostra <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uma <xref:System.ServiceModel.ServiceAuthorizationManager>implementação e , entre eles, conceder acesso a métodos específicos do serviço para usuários específicos. Esta amostra é baseada no Nome do Usuário de Segurança de <xref:System.ServiceModel.ServiceAuthorizationManager> [Mensagem,](../../../../docs/framework/wcf/samples/message-security-user-name.md)mas demonstra como realizar uma transformação de sinistro antes de ser chamada.

> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.

 Em resumo, esta amostra demonstra como:

- O cliente pode ser autenticado usando um nome de usuário-senha.

- O cliente pode ser autenticado usando um certificado X.509.

- O servidor valida as credenciais do cliente em um validador personalizado. `UsernamePassword`

- O servidor é autenticado usando o certificado X.509 do servidor.

- O servidor <xref:System.ServiceModel.ServiceAuthorizationManager> pode usar para controlar o acesso a certos métodos no serviço.

- Como implementar <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

O serviço expõe dois pontos finais para se comunicar com o serviço, definidos usando o arquivo de configuração App.config. Cada ponto final consiste em um endereço, um vinculativo e um contrato. Uma vinculação é configurada com uma vinculação padrão `wsHttpBinding` que usa a autenticação do WS-Security e do nome de usuário do cliente. A outra vinculação é `wsHttpBinding` configurada com uma vinculação padrão que usa a autenticação do WS-Security e do certificado do cliente. O [ \<comportamento>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) especifica que as credenciais do usuário devem ser usadas para autenticação de serviço. O certificado de servidor deve `SubjectName` conter o `findValue` mesmo valor para a propriedade que o atributo no [ \<serviçoCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
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
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

Cada configuração de ponto final do cliente consiste em um nome de configuração, um endereço absoluto para o ponto final do serviço, a vinculação e o contrato. A vinculação do cliente é configurada com o modo de segurança apropriado, conforme especificado neste caso no [ \<>de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) e `clientCredentialType` conforme especificado na [ \<mensagem>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

Para o ponto final baseado em nome de usuário, a implementação do cliente define o nome de usuário e a senha a serem usados.

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

Para o ponto final baseado em certificado, a implementação do cliente define o certificado do cliente a ser usado.

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

Esta amostra usa <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> um personalizado para validar nomes de usuário e senhas. Os implementos `MyCustomUserNamePasswordValidator`amostrais, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>derivados de . Consulte a <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> documentação sobre para obter mais informações. Com o propósito de demonstrar <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>a integração com o <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> , esta amostra validador personalizada implementa o método para aceitar pares de nome de usuário/senha onde o nome de usuário corresponde à senha como mostrado no código a seguir.

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
{
  // This method validates users. It allows in two users,
  // test1 and test2 with passwords 1tset and 2tset respectively.
  // This code is for illustration purposes only and
  // MUST NOT be used in a production environment because it
  // is NOT secure.
  public override void Validate(string userName, string password)
  {
    if (null == userName || null == password)
    {
      throw new ArgumentNullException();
    }

    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
    {
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

Uma vez que o validador seja implementado no código de serviço, o host de serviço deve ser informado sobre a instância do validador a ser usado. Isso é feito usando o seguinte código:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Ou você pode fazer a mesma coisa na configuração:

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

A Windows Communication Foundation (WCF) fornece um modelo rico baseado em sinistros para a realização de verificações de acesso. O <xref:System.ServiceModel.ServiceAuthorizationManager> objeto é usado para realizar a verificação de acesso e determinar se as reclamações associadas ao cliente satisfazem os requisitos necessários para acessar o método de serviço.

Para fins de demonstração, esta <xref:System.ServiceModel.ServiceAuthorizationManager> amostra mostra <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> uma implementação que implementa o método para `http://example.com/claims/allowedoperation` permitir o acesso do usuário a métodos baseados em reivindicações de tipo cujo valor é o URI de Ação da operação que é permitido ser chamado.

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

Uma vez <xref:System.ServiceModel.ServiceAuthorizationManager> implementado o personalizado, o host <xref:System.ServiceModel.ServiceAuthorizationManager> de serviço deve ser informado sobre o uso. Isso é feito como mostrado no código a seguir.

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

O <xref:System.IdentityModel.Policy.IAuthorizationPolicy> principal método a <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> ser implementado é o método.

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

O código anterior <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> mostra como o método verifica que nenhuma nova reivindicação foi adicionada que afeta o processamento e adiciona reivindicações específicas. As reivindicações permitidas são `GetAllowedOpList` obtidas a partir do método, que é implementado para retornar uma lista específica de operações que o usuário está autorizado a realizar. A política de autorização adiciona reivindicações para acesso à operação em particular. Isso é usado <xref:System.ServiceModel.ServiceAuthorizationManager> posteriormente pelo para realizar decisões de verificação de acesso.

Uma vez <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementado o costume, o host de serviço deve ser informado sobre as políticas de autorização a serem usados.

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. O cliente chama com sucesso os métodos Adicionar, Subtrair e Vários e recebe uma mensagem "O acesso é negado" ao tentar chamar o método 'Dividir'. Pressione ENTER na janela do cliente para desligar o cliente.

## <a name="setup-batch-file"></a>Arquivo de lote de configuração

O arquivo de lote Setup.bat incluído nesta amostra permite configurar o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer segurança baseada em certificados de servidor.

O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote para que eles possam ser modificados para serem executados na configuração apropriada:

- Criando o certificado do servidor.

    As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado. A variável %SERVER_NAME% especifica o nome do servidor. Altere essa variável para especificar o nome do seu próprio servidor. O valor padrão é localhost.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalando o certificado do servidor na loja de certificados confiáveis do cliente.

    As seguintes linhas no arquivo de lote Setup.bat copiam o certificado do servidor na loja de pessoas confiáveis do cliente. Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente. Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Criando o certificado do cliente.

    As seguintes linhas do arquivo setup.bat batch criam o certificado cliente a ser usado. A variável %USER_NAME% especifica o nome do servidor. Este valor é definido como "test1" `IAuthorizationPolicy` porque este é o nome que o procura. Se você alterar o valor de %USER_NAME% você `IAuthorizationPolicy.Evaluate` deve alterar o valor correspondente no método.

    O certificado é armazenado na minha loja (pessoal) sob a localização da loja CurrentUser.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalando o certificado de cliente na loja de certificados confiáveis do servidor.

    As seguintes linhas no arquivo de lote Setup.bat copiam o certificado do cliente na loja de pessoas confiáveis. Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema de servidor. Se você já tiver um certificado enraizado em um certificado raiz confiável — por exemplo, um certificado emitido pela Microsoft — essa etapa de preencher a loja de certificados do servidor com o certificado do cliente não é necessária.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Para configurar e construir a amostra

1. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Para executar a amostra em uma configuração de computador único ou cruzado, use as seguintes instruções.

> [!NOTE]
> Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.

### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar a amostra no mesmo computador

1. Abrir o prompt de comando do desenvolvedor para o Visual Studio com privilégios de administrador e executar *Setup.bat* a partir da pasta de instalação de amostra. Isso instala todos os certificados necessários para a execução da amostra.

    > [!NOTE]
    > O arquivo de lote Setup.bat foi projetado para ser executado a partir do Prompt de comando do desenvolvedor para o Visual Studio. A variável de ambiente PATH definida no Prompt de comando do desenvolvedor para visual studio aponta para o diretório que contém executáveis exigidos pelo script *Setup.bat.*

1. Launch Service.exe from *service\bin*.

1. Inicie client.exe a *partir de \client\bin*. A atividade do cliente é exibida no aplicativo do console cliente.

Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Para executar a amostra através de computadores

1. Crie um diretório no computador de serviço.

2. Copie os arquivos do programa de serviço de *\service\bin* para o diretório no computador de serviço. Copie também os arquivos Setup.bat, Cleanup.bat, GetComputerName.vbs e ImportClientCert.bat para o computador de serviço.

3. Crie um diretório no computador cliente para os binários do cliente.

4. Copie os arquivos do programa cliente para o diretório do cliente no computador cliente. Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.

5. No servidor, `setup.bat service` execute no Prompt de comando do desenvolvedor para o Visual Studio aberto com privilégios de administrador.

    A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado *Service.cer*.

6. Editar *Service.exe.config* para refletir o novo `findValue` nome do certificado (no atributo no [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador. Também altere o \<nome do\< **computador** no serviço>/baseEndereços> elemento do localhost para o nome totalmente qualificado do seu computador de serviço.

7. Copie o arquivo *Service.cer* do diretório de serviço para o diretório do cliente no computador cliente.

8. No cliente, `setup.bat client` execute no Prompt de Comando de Desenvolvedor para visual Studio aberto com privilégios de administrador.

    A `setup.bat` execução com o `client` argumento cria um certificado de cliente chamado **test1** e exporta o certificado do cliente para um arquivo chamado *Client.cer*.

9. No arquivo *Client.exe.config* no computador do cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço. Faça isso substituindo **o localhost** pelo nome de domínio totalmente qualificado do servidor.

10. Copie o arquivo Client.cer do diretório do cliente para o diretório de serviço situado no servidor.

11. No cliente, execute *ImportServiceCert.bat* no Prompt de comando do desenvolvedor para o Visual Studio aberto com privilégios de administrador.

    Isso importa o certificado de serviço do arquivo Service.cer para a loja **CurrentUser - TrustedPeople.**

12. No servidor, execute *ImportClientCert.bat* no Prompt de comando do desenvolvedor para o Visual Studio aberto com privilégios de administrador.

    Isso importa o certificado do cliente do arquivo Client.cer para a loja **LocalMachine - TrustedPeople.**

13. No computador do servidor, inicie Service.exe a partir da janela de solicitação de comando.

14. No computador do cliente, inicie client.exe a partir de uma janela de solicitação de comando.

    Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="clean-up-after-the-sample"></a>Limpe depois da amostra

Para limpar após a amostra, execute *Cleanup.bat* na pasta amostras quando terminar de executar a amostra. Isso remove os certificados de servidor e cliente da loja de certificados.

> [!NOTE]
> Este script não remove certificados de serviço em um cliente ao executar essa amostra em computadores. Se você tiver executado amostras wcf que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople. Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` seguinte comando: Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
