---
title: Política de autorização
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 16549b90692d8061abe729521075e0f248446513
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873473"
---
# <a name="authorization-policy"></a>Política de autorização

Este exemplo demonstra como implementar uma política de autorização de declaração personalizada e um Gerenciador de autorização de serviço personalizado associado. Isso é útil quando o acesso baseado em declarações verifica a operações de serviço e antes das verificações de acesso, a serviço torna concede ao chamador determinados direitos. Este exemplo mostra o processo de adição de declarações, bem como o processo para fazer uma verificação de acesso em relação ao conjunto finalizado de declarações. Todas as mensagens de aplicativo entre o cliente e servidor assinadas e criptografadas. Por padrão com o `wsHttpBinding` , um nome de usuário e senha fornecidos pelo cliente são usadas para fazer logon em uma conta válida do Windows NT. Este exemplo demonstra como utilizar um personalizado <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para autenticar o cliente. Além disso, este exemplo mostra o cliente autenticar para o serviço usando um certificado X.509. Este exemplo mostra uma implementação de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e <xref:System.ServiceModel.ServiceAuthorizationManager>, que entre eles conceder acesso aos métodos específicos do serviço para usuários específicos. Este exemplo é baseado na [nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md), mas demonstra como executar uma transformação de declaração antes do <xref:System.ServiceModel.ServiceAuthorizationManager> que está sendo chamado.

> [!NOTE]
> As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.

 Em resumo, este exemplo demonstra como:

-   O cliente pode ser autenticado usando uma senha de nome de usuário.

-   O cliente pode ser autenticado usando um certificado X.509.

-   O servidor valida as credenciais do cliente em relação a um personalizado `UsernamePassword` validador.

-   O servidor é autenticado usando o certificado do servidor x. 509.

-   O servidor pode usar <xref:System.ServiceModel.ServiceAuthorizationManager> para controlar o acesso a determinados métodos no serviço.

-   Como implementar <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

O serviço expõe dois pontos de extremidade para se comunicar com o serviço, definido usando o arquivo de configuração App. config. Cada ponto de extremidade consiste em um endereço, uma ligação e um contrato. Uma associação está configurada com um padrão `wsHttpBinding` associação que usa a autenticação de nome de usuário do WS-Security e o cliente. A outra associação está configurada com um padrão `wsHttpBinding` associação que usa a autenticação de certificado do WS-Security e o cliente. O [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Especifica que as credenciais do usuário devem ser usados para autenticação de serviço. O certificado do servidor deve conter o mesmo valor para o `SubjectName` a propriedade como o `findValue` atributo na [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

Cada configuração de ponto de extremidade cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato. A associação de cliente está configurado com o modo de segurança apropriados, conforme especificado neste caso na [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) e `clientCredentialType` conforme especificado no [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).

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

Da empresa com base no nome de usuário, a implementação do cliente define o nome de usuário e senha a ser usada.

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

O ponto de extremidade com base em certificado, a implementação do cliente define o certificado do cliente para usar.

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

Este exemplo usa um <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para validar nomes de usuário e senhas. O exemplo implementa `MyCustomUserNamePasswordValidator`, derivado do <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Consulte a documentação <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para obter mais informações. Para fins de demonstração da integração com o <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, este validador personalizado de exemplo implementa o <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> método para aceitar os pares de nome/senha de usuário em que o nome de usuário corresponde à senha, conforme mostrado no código a seguir.

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

Depois que o validador é implementado no código de serviço, o host de serviço deve ser informado sobre a instância do validador para usar. Isso é feito usando o seguinte código:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Ou você pode fazer a mesma coisa na configuração:

```xml
<behavior ...>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation (WCF) fornece um rico modelo baseado em declarações para executar verificações de acesso. O <xref:System.ServiceModel.ServiceAuthorizationManager> objeto é usado para executar a verificação de acesso e determinar se as declarações associadas com o cliente satisfazem os requisitos necessários para acessar o método de serviço.

Para fins de demonstração, este exemplo mostra uma implementação de <xref:System.ServiceModel.ServiceAuthorizationManager> que implementa o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método para permitir o acesso do usuário aos métodos com base em declarações de tipo `http://example.com/claims/allowedoperation` cujo valor é o URI de ação da operação que é pode ser chamado.

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

Uma vez personalizado <xref:System.ServiceModel.ServiceAuthorizationManager> é implementado, o host de serviço deve ser informado sobre o <xref:System.ServiceModel.ServiceAuthorizationManager> usar. Isso é feito conforme mostrado no código a seguir.

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

O principal <xref:System.IdentityModel.Policy.IAuthorizationPolicy> é o método para implementar o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método.

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

Mostra o código anterior como o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método verifica se nenhuma nova declaração foram adicionadas que afeta o processamento e adiciona declarações específicas. As declarações que são permitidas são obtidas a partir de `GetAllowedOpList` método, que é implementado para retornar uma lista específica de operações que o usuário tem permissão para executar. A política de autorização adiciona declarações para acessar a operação específica. Isso é usado posteriormente pelo <xref:System.ServiceModel.ServiceAuthorizationManager> para executar as decisões de verificação de acesso.

Uma vez personalizado <xref:System.IdentityModel.Policy.IAuthorizationPolicy> é implementado, o host de serviço deve ser informado sobre as políticas de autorização para usar.

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. O cliente chama a adicionar, subtrair e vários métodos e recebe uma mensagem de "Acesso negado" ao tentar chamar o método de divisão com êxito. Pressione ENTER na janela do cliente para desligar o cliente.

## <a name="setup-batch-file"></a>Arquivo de lote

O arquivo em lotes de Setup. bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo hospedado internamente que exige a segurança baseada em certificado do servidor.

O exemplo a seguir fornece uma visão geral das diferentes seções dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada:

-   Criando o certificado do servidor.

     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado. A variável % SERVER_NAME % Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. O valor padrão é localhost.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Instalando o certificado do servidor no repositório de certificados confiáveis do cliente.

     As seguintes linhas na cópia de arquivo de lote o certificado do servidor Setup. bat as pessoas confiáveis do cliente ao repositório. Esta etapa é necessária porque certificados que são gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   Criando o certificado do cliente.

     As seguintes linhas do arquivo em lotes bat criam o certificado do cliente a ser usado. A variável % nome_do_usuário % Especifica o nome do servidor. Esse valor é definido como "test1", porque esse é o nome de `IAuthorizationPolicy` procura. Se você alterar o valor de % nome_do_usuário %, você deve alterar o valor correspondente no `IAuthorizationPolicy.Evaluate` método.

     O certificado é armazenado no repositório My (pessoal) sob o local do repositório CurrentUser.

    ```
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   Instalando o certificado do cliente no repositório de certificados confiáveis do servidor.

     As seguintes linhas no arquivo em lotes bat copie o certificado do cliente para o armazenamento de pessoas confiáveis. Essa etapa é necessária porque os certificados que são gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do servidor. Se você já tiver um certificado que está enraizado em um certificado raiz confiável — por exemplo, um certificado da Microsoft emitido — essa etapa de preencher o repositório de certificados do servidor com o certificado do cliente não é necessária.

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Para configurar e compilar o exemplo

1. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Para executar o exemplo em uma configuração ou entre computadores, use as instruções a seguir.

> [!NOTE]
> Se você usar Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.

### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador

1. Abra o Prompt de comando do desenvolvedor para Visual Studio com privilégios de administrador e execute *Setup. bat* da pasta de instalação de exemplo. Essa opção instala todos os certificados necessários para executar o exemplo.

    > [!NOTE]
    > O arquivo em lotes de Setup. bat foi projetado para ser executado no Prompt de comando do desenvolvedor para Visual Studio. A variável de ambiente PATH definido no Prompt de comando do desenvolvedor para Visual Studio aponta para o diretório que contém os executáveis necessários para o *Setup. bat* script.

1. Iniciar Service.exe partir *service\bin*.

1. Iniciar Client.exe partir *\Client\Bin*. Atividade do cliente é exibida no aplicativo de console do cliente.

  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).

### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores

1. Crie um diretório no computador do serviço.

2. Copie os arquivos de programa de serviço da *\service\bin* para o diretório no computador do serviço. Também copie os arquivos Setup. bat, CleanUp, GetComputerName.vbs e ImportClientCert.bat para o computador do serviço.

3. Crie um diretório no computador cliente para os binários do cliente.

4. Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente. Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.

5. No servidor, execute `setup.bat service` no Prompt de comando desenvolvedor para Visual Studio aberto com privilégios de administrador.

   Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado *Service.cer*.

6. Editar *Service.exe.config* para refletir o novo nome do certificado (na `findValue` de atributo no [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador. Também alterar o **NomeDoComputador** na \<serviço > /\<baseAddresses > elemento do localhost como o nome totalmente qualificado do seu computador de serviço.

7. Cópia de *Service.cer* arquivo do diretório de serviço para o diretório do cliente no computador cliente.

8. No cliente, execute `setup.bat client` no Prompt de comando desenvolvedor para Visual Studio aberto com privilégios de administrador.

   Executando `setup.bat` com o `client` argumento cria um certificado de cliente denominado **test1** e exporta o certificado do cliente para um arquivo chamado *cer*.

9. No *Client.exe.config* file no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço. Para fazer isso, substituindo **localhost** com o nome de domínio totalmente qualificado do servidor.

10. Copie o arquivo de Client. cer do diretório do cliente para o diretório de serviço no servidor.

11. No cliente, execute *ImportServiceCert.bat* no Prompt de comando desenvolvedor para Visual Studio aberto com privilégios de administrador.

   Este importa o certificado de serviço do arquivo Service.cer nos **CurrentUser - TrustedPeople** armazenar.

12. No servidor, execute *ImportClientCert.bat* no Prompt de comando desenvolvedor para Visual Studio aberto com privilégios de administrador.

   Isso importa o certificado do cliente do arquivo CER para o **LocalMachine - TrustedPeople** armazenar.

13. No computador do servidor, inicie Service.exe da janela de prompt de comando.

14. No computador cliente, inicie Client.exe em uma janela do prompt de comando.

   Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).

### <a name="clean-up-after-the-sample"></a>Limpar após a amostra

Para limpar após a amostra, execute *CleanUp* na pasta exemplos quando você terminar a execução do exemplo. Isso remove os certificados de servidor e cliente do repositório de certificados.

> [!NOTE]
> Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores. Se você executou os exemplos do WCF que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople armazenar. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.