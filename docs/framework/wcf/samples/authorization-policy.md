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
# <a name="authorization-policy"></a><span data-ttu-id="471ae-102">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="471ae-102">Authorization Policy</span></span>

<span data-ttu-id="471ae-103">Esta amostra demonstra como implementar uma política de autorização de sinistro personalizado e um gerente de autorização de serviço personalizado associado.</span><span class="sxs-lookup"><span data-stu-id="471ae-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="471ae-104">Isso é útil quando o serviço faz verificações de acesso baseadas em sinistros às operações de serviço e antes das verificações de acesso, concede ao chamador certos direitos.</span><span class="sxs-lookup"><span data-stu-id="471ae-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="471ae-105">Esta amostra mostra tanto o processo de adição de sinistros quanto o processo para fazer uma verificação de acesso em relação ao conjunto de sinistros finalizado.</span><span class="sxs-lookup"><span data-stu-id="471ae-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="471ae-106">Todas as mensagens de aplicativo entre o cliente e o servidor são assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="471ae-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="471ae-107">Por padrão, `wsHttpBinding` com a vinculação, um nome de usuário e senha fornecidos pelo cliente são usados para fazer logon em uma conta válida do Windows NT.</span><span class="sxs-lookup"><span data-stu-id="471ae-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="471ae-108">Esta amostra demonstra como <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> utilizar um costume para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="471ae-109">Além disso, esta amostra mostra o cliente autenticando-se ao serviço usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="471ae-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="471ae-110">Esta amostra mostra <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uma <xref:System.ServiceModel.ServiceAuthorizationManager>implementação e , entre eles, conceder acesso a métodos específicos do serviço para usuários específicos.</span><span class="sxs-lookup"><span data-stu-id="471ae-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="471ae-111">Esta amostra é baseada no Nome do Usuário de Segurança de <xref:System.ServiceModel.ServiceAuthorizationManager> [Mensagem,](../../../../docs/framework/wcf/samples/message-security-user-name.md)mas demonstra como realizar uma transformação de sinistro antes de ser chamada.</span><span class="sxs-lookup"><span data-stu-id="471ae-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="471ae-112">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="471ae-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="471ae-113">Em resumo, esta amostra demonstra como:</span><span class="sxs-lookup"><span data-stu-id="471ae-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="471ae-114">O cliente pode ser autenticado usando um nome de usuário-senha.</span><span class="sxs-lookup"><span data-stu-id="471ae-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="471ae-115">O cliente pode ser autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="471ae-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="471ae-116">O servidor valida as credenciais do cliente em um validador personalizado. `UsernamePassword`</span><span class="sxs-lookup"><span data-stu-id="471ae-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="471ae-117">O servidor é autenticado usando o certificado X.509 do servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="471ae-118">O servidor <xref:System.ServiceModel.ServiceAuthorizationManager> pode usar para controlar o acesso a certos métodos no serviço.</span><span class="sxs-lookup"><span data-stu-id="471ae-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="471ae-119">Como implementar <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="471ae-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="471ae-120">O serviço expõe dois pontos finais para se comunicar com o serviço, definidos usando o arquivo de configuração App.config. Cada ponto final consiste em um endereço, um vinculativo e um contrato.</span><span class="sxs-lookup"><span data-stu-id="471ae-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="471ae-121">Uma vinculação é configurada com uma vinculação padrão `wsHttpBinding` que usa a autenticação do WS-Security e do nome de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="471ae-122">A outra vinculação é `wsHttpBinding` configurada com uma vinculação padrão que usa a autenticação do WS-Security e do certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="471ae-123">O [ \<comportamento>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) especifica que as credenciais do usuário devem ser usadas para autenticação de serviço.</span><span class="sxs-lookup"><span data-stu-id="471ae-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="471ae-124">O certificado de servidor deve `SubjectName` conter o `findValue` mesmo valor para a propriedade que o atributo no [ \<serviçoCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="471ae-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="471ae-125">Cada configuração de ponto final do cliente consiste em um nome de configuração, um endereço absoluto para o ponto final do serviço, a vinculação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="471ae-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="471ae-126">A vinculação do cliente é configurada com o modo de segurança apropriado, conforme especificado neste caso no [ \<>de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) e `clientCredentialType` conforme especificado na [ \<mensagem>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="471ae-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="471ae-127">Para o ponto final baseado em nome de usuário, a implementação do cliente define o nome de usuário e a senha a serem usados.</span><span class="sxs-lookup"><span data-stu-id="471ae-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="471ae-128">Para o ponto final baseado em certificado, a implementação do cliente define o certificado do cliente a ser usado.</span><span class="sxs-lookup"><span data-stu-id="471ae-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="471ae-129">Esta amostra usa <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> um personalizado para validar nomes de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="471ae-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="471ae-130">Os implementos `MyCustomUserNamePasswordValidator`amostrais, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>derivados de .</span><span class="sxs-lookup"><span data-stu-id="471ae-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="471ae-131">Consulte a <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> documentação sobre para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="471ae-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="471ae-132">Com o propósito de demonstrar <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>a integração com o <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> , esta amostra validador personalizada implementa o método para aceitar pares de nome de usuário/senha onde o nome de usuário corresponde à senha como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="471ae-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="471ae-133">Uma vez que o validador seja implementado no código de serviço, o host de serviço deve ser informado sobre a instância do validador a ser usado.</span><span class="sxs-lookup"><span data-stu-id="471ae-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="471ae-134">Isso é feito usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="471ae-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="471ae-135">Ou você pode fazer a mesma coisa na configuração:</span><span class="sxs-lookup"><span data-stu-id="471ae-135">Or you can do the same thing in configuration:</span></span>

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

<span data-ttu-id="471ae-136">A Windows Communication Foundation (WCF) fornece um modelo rico baseado em sinistros para a realização de verificações de acesso.</span><span class="sxs-lookup"><span data-stu-id="471ae-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="471ae-137">O <xref:System.ServiceModel.ServiceAuthorizationManager> objeto é usado para realizar a verificação de acesso e determinar se as reclamações associadas ao cliente satisfazem os requisitos necessários para acessar o método de serviço.</span><span class="sxs-lookup"><span data-stu-id="471ae-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="471ae-138">Para fins de demonstração, esta <xref:System.ServiceModel.ServiceAuthorizationManager> amostra mostra <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> uma implementação que implementa o método para `http://example.com/claims/allowedoperation` permitir o acesso do usuário a métodos baseados em reivindicações de tipo cujo valor é o URI de Ação da operação que é permitido ser chamado.</span><span class="sxs-lookup"><span data-stu-id="471ae-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="471ae-139">Uma vez <xref:System.ServiceModel.ServiceAuthorizationManager> implementado o personalizado, o host <xref:System.ServiceModel.ServiceAuthorizationManager> de serviço deve ser informado sobre o uso.</span><span class="sxs-lookup"><span data-stu-id="471ae-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="471ae-140">Isso é feito como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="471ae-140">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="471ae-141">O <xref:System.IdentityModel.Policy.IAuthorizationPolicy> principal método a <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> ser implementado é o método.</span><span class="sxs-lookup"><span data-stu-id="471ae-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="471ae-142">O código anterior <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> mostra como o método verifica que nenhuma nova reivindicação foi adicionada que afeta o processamento e adiciona reivindicações específicas.</span><span class="sxs-lookup"><span data-stu-id="471ae-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="471ae-143">As reivindicações permitidas são `GetAllowedOpList` obtidas a partir do método, que é implementado para retornar uma lista específica de operações que o usuário está autorizado a realizar.</span><span class="sxs-lookup"><span data-stu-id="471ae-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="471ae-144">A política de autorização adiciona reivindicações para acesso à operação em particular.</span><span class="sxs-lookup"><span data-stu-id="471ae-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="471ae-145">Isso é usado <xref:System.ServiceModel.ServiceAuthorizationManager> posteriormente pelo para realizar decisões de verificação de acesso.</span><span class="sxs-lookup"><span data-stu-id="471ae-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="471ae-146">Uma vez <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementado o costume, o host de serviço deve ser informado sobre as políticas de autorização a serem usados.</span><span class="sxs-lookup"><span data-stu-id="471ae-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="471ae-147">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="471ae-148">O cliente chama com sucesso os métodos Adicionar, Subtrair e Vários e recebe uma mensagem "O acesso é negado" ao tentar chamar o método 'Dividir'.</span><span class="sxs-lookup"><span data-stu-id="471ae-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="471ae-149">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="471ae-150">Arquivo de lote de configuração</span><span class="sxs-lookup"><span data-stu-id="471ae-150">Setup Batch File</span></span>

<span data-ttu-id="471ae-151">O arquivo de lote Setup.bat incluído nesta amostra permite configurar o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer segurança baseada em certificados de servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="471ae-152">O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote para que eles possam ser modificados para serem executados na configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="471ae-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="471ae-153">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-153">Creating the server certificate.</span></span>

    <span data-ttu-id="471ae-154">As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="471ae-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="471ae-155">A variável %SERVER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="471ae-156">Altere essa variável para especificar o nome do seu próprio servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="471ae-157">O valor padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="471ae-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="471ae-158">Instalando o certificado do servidor na loja de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="471ae-159">As seguintes linhas no arquivo de lote Setup.bat copiam o certificado do servidor na loja de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="471ae-160">Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="471ae-161">Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="471ae-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="471ae-162">Criando o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-162">Creating the client certificate.</span></span>

    <span data-ttu-id="471ae-163">As seguintes linhas do arquivo setup.bat batch criam o certificado cliente a ser usado.</span><span class="sxs-lookup"><span data-stu-id="471ae-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="471ae-164">A variável %USER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="471ae-165">Este valor é definido como "test1" `IAuthorizationPolicy` porque este é o nome que o procura.</span><span class="sxs-lookup"><span data-stu-id="471ae-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="471ae-166">Se você alterar o valor de %USER_NAME% você `IAuthorizationPolicy.Evaluate` deve alterar o valor correspondente no método.</span><span class="sxs-lookup"><span data-stu-id="471ae-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="471ae-167">O certificado é armazenado na minha loja (pessoal) sob a localização da loja CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="471ae-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="471ae-168">Instalando o certificado de cliente na loja de certificados confiáveis do servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="471ae-169">As seguintes linhas no arquivo de lote Setup.bat copiam o certificado do cliente na loja de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="471ae-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="471ae-170">Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema de servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="471ae-171">Se você já tiver um certificado enraizado em um certificado raiz confiável — por exemplo, um certificado emitido pela Microsoft — essa etapa de preencher a loja de certificados do servidor com o certificado do cliente não é necessária.</span><span class="sxs-lookup"><span data-stu-id="471ae-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="471ae-172">Para configurar e construir a amostra</span><span class="sxs-lookup"><span data-stu-id="471ae-172">To set up and build the sample</span></span>

1. <span data-ttu-id="471ae-173">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="471ae-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="471ae-174">Para executar a amostra em uma configuração de computador único ou cruzado, use as seguintes instruções.</span><span class="sxs-lookup"><span data-stu-id="471ae-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="471ae-175">Se você usar Svcutil.exe para regenerar a configuração desta amostra, certifique-se de modificar o nome do ponto final na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="471ae-176">Para executar a amostra no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="471ae-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="471ae-177">Abrir o prompt de comando do desenvolvedor para o Visual Studio com privilégios de administrador e executar *Setup.bat* a partir da pasta de instalação de amostra.</span><span class="sxs-lookup"><span data-stu-id="471ae-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="471ae-178">Isso instala todos os certificados necessários para a execução da amostra.</span><span class="sxs-lookup"><span data-stu-id="471ae-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="471ae-179">O arquivo de lote Setup.bat foi projetado para ser executado a partir do Prompt de comando do desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="471ae-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="471ae-180">A variável de ambiente PATH definida no Prompt de comando do desenvolvedor para visual studio aponta para o diretório que contém executáveis exigidos pelo script *Setup.bat.*</span><span class="sxs-lookup"><span data-stu-id="471ae-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="471ae-181">Launch Service.exe from *service\bin*.</span><span class="sxs-lookup"><span data-stu-id="471ae-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="471ae-182">Inicie client.exe a *partir de \client\bin*.</span><span class="sxs-lookup"><span data-stu-id="471ae-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="471ae-183">A atividade do cliente é exibida no aplicativo do console cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="471ae-184">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="471ae-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="471ae-185">Para executar a amostra através de computadores</span><span class="sxs-lookup"><span data-stu-id="471ae-185">To run the sample across computers</span></span>

1. <span data-ttu-id="471ae-186">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="471ae-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="471ae-187">Copie os arquivos do programa de serviço de *\service\bin* para o diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="471ae-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="471ae-188">Copie também os arquivos Setup.bat, Cleanup.bat, GetComputerName.vbs e ImportClientCert.bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="471ae-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="471ae-189">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="471ae-190">Copie os arquivos do programa cliente para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="471ae-191">Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="471ae-192">No servidor, `setup.bat service` execute no Prompt de comando do desenvolvedor para o Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="471ae-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="471ae-193">A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado *Service.cer*.</span><span class="sxs-lookup"><span data-stu-id="471ae-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="471ae-194">Editar *Service.exe.config* para refletir o novo `findValue` nome do certificado (no atributo no [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="471ae-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="471ae-195">Também altere o \<nome do\< **computador** no serviço>/baseEndereços> elemento do localhost para o nome totalmente qualificado do seu computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="471ae-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="471ae-196">Copie o arquivo *Service.cer* do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="471ae-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="471ae-197">No cliente, `setup.bat client` execute no Prompt de Comando de Desenvolvedor para visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="471ae-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="471ae-198">A `setup.bat` execução com o `client` argumento cria um certificado de cliente chamado **test1** e exporta o certificado do cliente para um arquivo chamado *Client.cer*.</span><span class="sxs-lookup"><span data-stu-id="471ae-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="471ae-199">No arquivo *Client.exe.config* no computador do cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="471ae-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="471ae-200">Faça isso substituindo **o localhost** pelo nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="471ae-201">Copie o arquivo Client.cer do diretório do cliente para o diretório de serviço situado no servidor.</span><span class="sxs-lookup"><span data-stu-id="471ae-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="471ae-202">No cliente, execute *ImportServiceCert.bat* no Prompt de comando do desenvolvedor para o Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="471ae-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="471ae-203">Isso importa o certificado de serviço do arquivo Service.cer para a loja **CurrentUser - TrustedPeople.**</span><span class="sxs-lookup"><span data-stu-id="471ae-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="471ae-204">No servidor, execute *ImportClientCert.bat* no Prompt de comando do desenvolvedor para o Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="471ae-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="471ae-205">Isso importa o certificado do cliente do arquivo Client.cer para a loja **LocalMachine - TrustedPeople.**</span><span class="sxs-lookup"><span data-stu-id="471ae-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="471ae-206">No computador do servidor, inicie Service.exe a partir da janela de solicitação de comando.</span><span class="sxs-lookup"><span data-stu-id="471ae-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="471ae-207">No computador do cliente, inicie client.exe a partir de uma janela de solicitação de comando.</span><span class="sxs-lookup"><span data-stu-id="471ae-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="471ae-208">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="471ae-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="471ae-209">Limpe depois da amostra</span><span class="sxs-lookup"><span data-stu-id="471ae-209">Clean up after the sample</span></span>

<span data-ttu-id="471ae-210">Para limpar após a amostra, execute *Cleanup.bat* na pasta amostras quando terminar de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="471ae-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="471ae-211">Isso remove os certificados de servidor e cliente da loja de certificados.</span><span class="sxs-lookup"><span data-stu-id="471ae-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="471ae-212">Este script não remove certificados de serviço em um cliente ao executar essa amostra em computadores.</span><span class="sxs-lookup"><span data-stu-id="471ae-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="471ae-213">Se você tiver executado amostras wcf que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="471ae-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="471ae-214">Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` seguinte comando: Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="471ae-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
