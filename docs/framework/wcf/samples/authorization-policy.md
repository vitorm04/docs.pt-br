---
title: Política de autorização
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: a789faae1f6224512f9a8a9ab084c8a82e4a2b87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553656"
---
# <a name="authorization-policy"></a><span data-ttu-id="bc895-102">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="bc895-102">Authorization Policy</span></span>

<span data-ttu-id="bc895-103">Este exemplo demonstra como implementar uma política de autorização de declaração personalizada e um Gerenciador de autorização de serviço personalizado associado.</span><span class="sxs-lookup"><span data-stu-id="bc895-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="bc895-104">Isso é útil quando o serviço faz verificações de acesso baseadas em declaração para operações de serviço e antes das verificações de acesso, concede ao chamador determinados direitos.</span><span class="sxs-lookup"><span data-stu-id="bc895-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="bc895-105">Este exemplo mostra o processo de adição de declarações, bem como o processo de fazer uma verificação de acesso em relação ao conjunto de declarações finalizado.</span><span class="sxs-lookup"><span data-stu-id="bc895-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="bc895-106">Todas as mensagens de aplicativo entre o cliente e o servidor são assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="bc895-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="bc895-107">Por padrão, com a `wsHttpBinding` associação, um nome de usuário e senha fornecidos pelo cliente são usados para fazer logon em uma conta válida do Windows NT.</span><span class="sxs-lookup"><span data-stu-id="bc895-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="bc895-108">Este exemplo demonstra como utilizar um personalizado <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="bc895-109">Além disso, este exemplo mostra o cliente que está Autenticando para o serviço usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="bc895-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="bc895-110">Este exemplo mostra uma implementação de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e <xref:System.ServiceModel.ServiceAuthorizationManager> , que entre eles concedem acesso a métodos específicos do serviço para usuários específicos.</span><span class="sxs-lookup"><span data-stu-id="bc895-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="bc895-111">Este exemplo é baseado no [nome de usuário de segurança da mensagem](message-security-user-name.md), mas demonstra como executar uma transformação de declaração antes da <xref:System.ServiceModel.ServiceAuthorizationManager> chamada.</span><span class="sxs-lookup"><span data-stu-id="bc895-111">This sample is based on the [Message Security User Name](message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="bc895-112">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bc895-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="bc895-113">Em resumo, este exemplo demonstra como:</span><span class="sxs-lookup"><span data-stu-id="bc895-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="bc895-114">O cliente pode ser autenticado usando um nome de usuário-senha.</span><span class="sxs-lookup"><span data-stu-id="bc895-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="bc895-115">O cliente pode ser autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="bc895-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="bc895-116">O servidor valida as credenciais do cliente em relação a um `UsernamePassword` validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="bc895-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="bc895-117">O servidor é autenticado usando o certificado X. 509 do servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="bc895-118">O servidor pode usar o <xref:System.ServiceModel.ServiceAuthorizationManager> para controlar o acesso a determinados métodos no serviço.</span><span class="sxs-lookup"><span data-stu-id="bc895-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="bc895-119">Como implementar <xref:System.IdentityModel.Policy.IAuthorizationPolicy> .</span><span class="sxs-lookup"><span data-stu-id="bc895-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="bc895-120">O serviço expõe dois pontos de extremidade para se comunicar com o serviço, definido usando o arquivo de configuração App.config. Cada ponto de extremidade consiste em um endereço, uma associação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="bc895-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="bc895-121">Uma associação é configurada com uma `wsHttpBinding` associação padrão que usa o WS-Security e a autenticação de nome de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="bc895-122">A outra associação é configurada com uma `wsHttpBinding` associação padrão que usa WS-Security e autenticação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="bc895-123">O [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) especifica que as credenciais de usuário devem ser usadas para autenticação de serviço.</span><span class="sxs-lookup"><span data-stu-id="bc895-123">The [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="bc895-124">O certificado do servidor deve conter o mesmo valor para a `SubjectName` propriedade que o `findValue` atributo no [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="bc895-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="bc895-125">Cada configuração de ponto de extremidade de cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="bc895-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="bc895-126">A associação de cliente é configurada com o modo de segurança apropriado, conforme especificado nesse caso, no [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) e `clientCredentialType` conforme especificado no [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="bc895-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="bc895-127">Para o ponto de extremidade baseado em nome de usuário, a implementação do cliente define o nome de usuário e a senha a serem usados.</span><span class="sxs-lookup"><span data-stu-id="bc895-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="bc895-128">Para o ponto de extremidade baseado em certificado, a implementação do cliente define o certificado do cliente a ser usado.</span><span class="sxs-lookup"><span data-stu-id="bc895-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="bc895-129">Este exemplo usa um personalizado <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para validar nomes de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="bc895-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="bc895-130">O exemplo implementa `MyCustomUserNamePasswordValidator` , derivado de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .</span><span class="sxs-lookup"><span data-stu-id="bc895-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="bc895-131">Consulte a documentação sobre <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="bc895-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="bc895-132">Para fins de demonstração da integração com o <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , este exemplo de validador personalizado implementa o <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> método para aceitar pares de nome de usuário/senha em que o nome de usuário corresponde à senha, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="bc895-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="bc895-133">Depois que o validador for implementado no código de serviço, o host de serviço deverá ser informado sobre a instância do validador a ser usada.</span><span class="sxs-lookup"><span data-stu-id="bc895-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="bc895-134">Isso é feito usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="bc895-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="bc895-135">Ou você pode fazer a mesma coisa na configuração:</span><span class="sxs-lookup"><span data-stu-id="bc895-135">Or you can do the same thing in configuration:</span></span>

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

<span data-ttu-id="bc895-136">O Windows Communication Foundation (WCF) fornece um modelo rico baseado em declarações para executar verificações de acesso.</span><span class="sxs-lookup"><span data-stu-id="bc895-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="bc895-137">O <xref:System.ServiceModel.ServiceAuthorizationManager> objeto é usado para executar a verificação de acesso e determinar se as declarações associadas ao cliente atendem aos requisitos necessários para acessar o método de serviço.</span><span class="sxs-lookup"><span data-stu-id="bc895-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="bc895-138">Para fins de demonstração, este exemplo mostra uma implementação do <xref:System.ServiceModel.ServiceAuthorizationManager> que implementa o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método para permitir o acesso de um usuário a métodos com base em declarações do tipo `http://example.com/claims/allowedoperation` cujo valor é o URI da ação que tem permissão para ser chamada.</span><span class="sxs-lookup"><span data-stu-id="bc895-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="bc895-139">Depois que o personalizado <xref:System.ServiceModel.ServiceAuthorizationManager> é implementado, o host de serviço deve ser informado sobre o <xref:System.ServiceModel.ServiceAuthorizationManager> a ser usado.</span><span class="sxs-lookup"><span data-stu-id="bc895-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="bc895-140">Isso é feito conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="bc895-140">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="bc895-141">O <xref:System.IdentityModel.Policy.IAuthorizationPolicy> método principal a ser implementado é o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método.</span><span class="sxs-lookup"><span data-stu-id="bc895-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="bc895-142">O código anterior mostra como o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método verifica se nenhuma declaração nova foi adicionada, o que afeta o processamento e adiciona declarações específicas.</span><span class="sxs-lookup"><span data-stu-id="bc895-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="bc895-143">As declarações que são permitidas são obtidas do `GetAllowedOpList` método, que é implementado para retornar uma lista específica de operações que o usuário tem permissão para executar.</span><span class="sxs-lookup"><span data-stu-id="bc895-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="bc895-144">A política de autorização adiciona declarações para acessar a operação específica.</span><span class="sxs-lookup"><span data-stu-id="bc895-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="bc895-145">Isso é usado posteriormente pelo <xref:System.ServiceModel.ServiceAuthorizationManager> para executar decisões de verificação de acesso.</span><span class="sxs-lookup"><span data-stu-id="bc895-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="bc895-146">Depois que o personalizado <xref:System.IdentityModel.Policy.IAuthorizationPolicy> é implementado, o host de serviço deve ser informado sobre as políticas de autorização a serem usadas.</span><span class="sxs-lookup"><span data-stu-id="bc895-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="bc895-147">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bc895-148">O cliente chama com êxito os métodos Add, subtrair e Multiple e obtém uma mensagem "acesso negado" ao tentar chamar o método de divisão.</span><span class="sxs-lookup"><span data-stu-id="bc895-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="bc895-149">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="bc895-150">Arquivo em lotes de instalação</span><span class="sxs-lookup"><span data-stu-id="bc895-150">Setup Batch File</span></span>

<span data-ttu-id="bc895-151">O arquivo em lotes Setup.bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="bc895-152">Veja a seguir uma breve visão geral das diferentes seções dos arquivos em lotes para que eles possam ser modificados para serem executados na configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="bc895-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="bc895-153">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-153">Creating the server certificate.</span></span>

    <span data-ttu-id="bc895-154">As linhas a seguir do arquivo de Setup.bat lote criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="bc895-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="bc895-155">A variável% SERVER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="bc895-156">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="bc895-157">O valor padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="bc895-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="bc895-158">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="bc895-159">As linhas a seguir no arquivo de Setup.bat lote copiam o certificado do servidor no repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="bc895-160">Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="bc895-161">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — esta etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="bc895-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="bc895-162">Criando o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-162">Creating the client certificate.</span></span>

    <span data-ttu-id="bc895-163">As linhas a seguir do arquivo de Setup.bat lote criam o certificado do cliente a ser usado.</span><span class="sxs-lookup"><span data-stu-id="bc895-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="bc895-164">A variável% USER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="bc895-165">Esse valor é definido como "test1" porque esse é o nome que o `IAuthorizationPolicy` procura.</span><span class="sxs-lookup"><span data-stu-id="bc895-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="bc895-166">Se você alterar o valor de% USER_NAME%, deverá alterar o valor correspondente no `IAuthorizationPolicy.Evaluate` método.</span><span class="sxs-lookup"><span data-stu-id="bc895-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="bc895-167">O certificado é armazenado no meu repositório (pessoal) no local de armazenamento CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="bc895-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="bc895-168">Instalando o certificado do cliente no repositório de certificados confiáveis do servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="bc895-169">As linhas a seguir no arquivo de Setup.bat lote copiam o certificado do cliente para o repositório de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="bc895-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="bc895-170">Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema de servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="bc895-171">Se você já tiver um certificado com raiz em um certificado raiz confiável — por exemplo, um certificado emitido pela Microsoft — esta etapa de popular o repositório de certificados do servidor com o certificado do cliente não será necessária.</span><span class="sxs-lookup"><span data-stu-id="bc895-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="bc895-172">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bc895-172">To set up and build the sample</span></span>

1. <span data-ttu-id="bc895-173">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bc895-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="bc895-174">Para executar o exemplo em uma configuração de computador único ou entre computadores, use as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="bc895-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="bc895-175">Se você usar Svcutil.exe para regenerar a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="bc895-176">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="bc895-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="bc895-177">Abra Prompt de Comando do Desenvolvedor para Visual Studio com privilégios de administrador e execute *Setup.bat* na pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="bc895-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="bc895-178">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="bc895-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bc895-179">O arquivo em lotes Setup.bat foi projetado para ser executado do Prompt de Comando do Desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc895-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="bc895-180">A variável de ambiente PATH definida no Prompt de Comando do Desenvolvedor para o Visual Studio aponta para o diretório que contém os executáveis exigidos pelo script *Setup.bat* .</span><span class="sxs-lookup"><span data-stu-id="bc895-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="bc895-181">Inicie Service.exe de *create\bin*.</span><span class="sxs-lookup"><span data-stu-id="bc895-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="bc895-182">Inicie o Client.exe de *\client\bin*.</span><span class="sxs-lookup"><span data-stu-id="bc895-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="bc895-183">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="bc895-184">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="bc895-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="bc895-185">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="bc895-185">To run the sample across computers</span></span>

1. <span data-ttu-id="bc895-186">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="bc895-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="bc895-187">Copie os arquivos de programa do serviço do *\service\bin* para o diretório no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="bc895-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="bc895-188">Copie também os arquivos Setup.bat, Cleanup.bat, GetComputerName. vbs e ImportClientCert.bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="bc895-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="bc895-189">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="bc895-190">Copie os arquivos de programa do cliente para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="bc895-191">Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="bc895-192">No servidor, execute `setup.bat service` no prompt de comando do desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="bc895-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="bc895-193">`setup.bat`A execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado *Service. cer*.</span><span class="sxs-lookup"><span data-stu-id="bc895-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="bc895-194">Edite *Service.exe.config* para refletir o novo nome de certificado (no `findValue` atributo no [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="bc895-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="bc895-195">Altere também o **ComputerName** no \<service> / \<baseAddresses> elemento do localhost para o nome totalmente qualificado do seu computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="bc895-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="bc895-196">Copie o arquivo *Service. cer* do diretório de serviço para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="bc895-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="bc895-197">No cliente, execute `setup.bat client` no prompt de comando do desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="bc895-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="bc895-198">`setup.bat`A execução com o `client` argumento cria um certificado de cliente chamado **Test1** e exporta o certificado do cliente para um arquivo chamado *Client. cer*.</span><span class="sxs-lookup"><span data-stu-id="bc895-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="bc895-199">No arquivo de *Client.exe.config* no computador cliente, altere o valor de endereço do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="bc895-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="bc895-200">Faça isso substituindo **localhost** pelo nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="bc895-201">Copie o arquivo client. cer do diretório cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="bc895-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="bc895-202">No cliente, execute *ImportServiceCert.bat* no prompt de comando do desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="bc895-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="bc895-203">Isso importa o certificado de serviço do arquivo Service. cer para o repositório **CurrentUser-TrustedPeople** .</span><span class="sxs-lookup"><span data-stu-id="bc895-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="bc895-204">No servidor, execute *ImportClientCert.bat* no prompt de comando do desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="bc895-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="bc895-205">Isso importa o certificado do cliente do arquivo client. cer para o repositório **LocalMachine-TrustedPeople** .</span><span class="sxs-lookup"><span data-stu-id="bc895-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="bc895-206">No computador servidor, inicie o Service.exe na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="bc895-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="bc895-207">No computador cliente, inicie o Client.exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="bc895-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="bc895-208">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="bc895-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="bc895-209">Limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="bc895-209">Clean up after the sample</span></span>

<span data-ttu-id="bc895-210">Para limpar após o exemplo, execute *Cleanup.bat* na pasta Samples quando terminar de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="bc895-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="bc895-211">Isso remove os certificados de cliente e servidor do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="bc895-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="bc895-212">Esse script não remove certificados de serviço em um cliente ao executar esse exemplo em computadores.</span><span class="sxs-lookup"><span data-stu-id="bc895-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="bc895-213">Se você tiver executado os exemplos do WCF que usam certificados entre computadores, certifique-se de limpar os certificados de serviço que foram instalados no repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="bc895-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="bc895-214">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="bc895-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
