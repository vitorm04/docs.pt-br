---
title: "Política de autorização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ba4548e6ea62f408fddf3629eca1318c482f728
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="authorization-policy"></a><span data-ttu-id="33d7c-102">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="33d7c-102">Authorization Policy</span></span>
<span data-ttu-id="33d7c-103">Este exemplo demonstra como implementar uma política de autorização de declaração personalizada e um Gerenciador de autorização de serviço personalizado associado.</span><span class="sxs-lookup"><span data-stu-id="33d7c-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="33d7c-104">Isso é útil quando a verificações de acesso baseado em declarações para operações de serviço e antes das verificações de acesso, você torna serviço concede o chamador certos direitos.</span><span class="sxs-lookup"><span data-stu-id="33d7c-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="33d7c-105">Este exemplo mostra o processo de adição de declarações, bem como o processo para fazer uma verificação de acesso em relação ao finalizadas conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="33d7c-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="33d7c-106">Todas as mensagens de aplicativo entre o cliente e servidor assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="33d7c-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="33d7c-107">Por padrão, com o `wsHttpBinding` ligação, um nome de usuário e senha fornecidos pelo cliente são usados para fazer logon para uma conta válida do Windows NT.</span><span class="sxs-lookup"><span data-stu-id="33d7c-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="33d7c-108">Este exemplo demonstra como utilizar um personalizado <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-108">This sample demonstrates how to utilize a custom <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` to authenticate the client.</span></span> <span data-ttu-id="33d7c-109">Além disso, este exemplo mostra o cliente autenticar para o serviço usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="33d7c-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="33d7c-110">Este exemplo mostra uma implementação de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e <xref:System.ServiceModel.ServiceAuthorizationManager>, que entre eles conceder acesso aos métodos específicos do serviço para usuários específicos.</span><span class="sxs-lookup"><span data-stu-id="33d7c-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="33d7c-111">Este exemplo é baseado no [nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md), mas demonstra como executar uma transformação de declaração antes do <xref:System.ServiceModel.ServiceAuthorizationManager> que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="33d7c-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33d7c-112">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="33d7c-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="33d7c-113">Em resumo, este exemplo demonstra como:</span><span class="sxs-lookup"><span data-stu-id="33d7c-113">In summary, this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="33d7c-114">O cliente pode ser autenticado usando uma senha e nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="33d7c-114">The client can be authenticated using a user name-password.</span></span>  
  
-   <span data-ttu-id="33d7c-115">O cliente pode ser autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="33d7c-115">The client can be authenticated using an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="33d7c-116">O servidor valida as credenciais do cliente em relação a um personalizado `UsernamePassword` validador.</span><span class="sxs-lookup"><span data-stu-id="33d7c-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>  
  
-   <span data-ttu-id="33d7c-117">O servidor é autenticado usando o certificado do servidor x. 509.</span><span class="sxs-lookup"><span data-stu-id="33d7c-117">The server is authenticated using the server's X.509 certificate.</span></span>  
  
-   <span data-ttu-id="33d7c-118">O servidor pode usar <xref:System.ServiceModel.ServiceAuthorizationManager> para controlar o acesso a determinados métodos no serviço.</span><span class="sxs-lookup"><span data-stu-id="33d7c-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>  
  
-   <span data-ttu-id="33d7c-119">Como implementar <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="33d7c-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
 <span data-ttu-id="33d7c-120">O serviço expõe dois pontos de extremidade de comunicação com o serviço, definido usando o arquivo de configuração App. config. Cada ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="33d7c-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="33d7c-121">Uma associação é configurada com um padrão `wsHttpBinding` associação que usa autenticação de nome de usuário do cliente e WS-Security.</span><span class="sxs-lookup"><span data-stu-id="33d7c-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="33d7c-122">Outra associação está configurada com um padrão `wsHttpBinding` associação que usa autenticação de certificado de cliente e WS-Security.</span><span class="sxs-lookup"><span data-stu-id="33d7c-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="33d7c-123">O [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Especifica que as credenciais do usuário a ser usado para autenticação do serviço.</span><span class="sxs-lookup"><span data-stu-id="33d7c-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="33d7c-124">O certificado do servidor deve conter o mesmo valor para o `SubjectName` a propriedade como o `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="33d7c-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="33d7c-125">Cada configuração de ponto de extremidade do cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="33d7c-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="33d7c-126">A ligação do cliente é configurado com o modo de segurança apropriadas conforme especificado nesse caso no [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) e `clientCredentialType` conforme especificado no [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="33d7c-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>  
  
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
  
 <span data-ttu-id="33d7c-127">Da empresa com base em nome de usuário, a implementação de cliente define o nome de usuário e senha a ser usada.</span><span class="sxs-lookup"><span data-stu-id="33d7c-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>  
  
```  
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
  
 <span data-ttu-id="33d7c-128">O ponto de extremidade com base em certificado, a implementação de cliente define o certificado de cliente para usar.</span><span class="sxs-lookup"><span data-stu-id="33d7c-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>  
  
```  
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
  
 <span data-ttu-id="33d7c-129">Este exemplo usa um personalizado <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para validar nomes de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="33d7c-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="33d7c-130">O exemplo implementa `MyCustomUserNamePasswordValidator`, derivada de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="33d7c-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="33d7c-131">Consulte a documentação <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="33d7c-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="33d7c-132">Para fins de demonstração da integração com o <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, este exemplo de validador personalizado implementa o <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> método para aceitar os pares de nome e senha de usuário onde o nome de usuário corresponde à senha, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="33d7c-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="33d7c-133">Depois que o validador é implementado no código de serviço, o host de serviço deve ser informado sobre a instância de validação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="33d7c-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="33d7c-134">Isso é feito usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="33d7c-134">This is done using the following code.</span></span>  
  
```  
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();  
```  
  
 <span data-ttu-id="33d7c-135">Ou você pode fazer a mesma coisa na configuração.</span><span class="sxs-lookup"><span data-stu-id="33d7c-135">Or you can do the same thing in configuration.</span></span>  
  
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
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="33d7c-136">Fornece um modelo de baseada em declarações avançado para executar verificações de acesso.</span><span class="sxs-lookup"><span data-stu-id="33d7c-136"> provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="33d7c-137">O <xref:System.ServiceModel.ServiceAuthorizationManager> objeto é usado para realizar a verificação de acesso e determinar se as declarações associadas ao cliente satisfazem os requisitos necessários para acessar o método de serviço.</span><span class="sxs-lookup"><span data-stu-id="33d7c-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>  
  
 <span data-ttu-id="33d7c-138">Para fins de demonstração, este exemplo mostra uma implementação de <xref:System.ServiceModel.ServiceAuthorizationManager> que implementa o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método para permitir o acesso do usuário aos métodos com base em declarações de tipo http://example.com/claims/allowedoperation cujo valor é a ação URI da operação que pode ser chamado.</span><span class="sxs-lookup"><span data-stu-id="33d7c-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type http://example.com/claims/allowedoperation whose value is the Action URI of the operation that is allowed to be called.</span></span>  
  
```  
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
  
 <span data-ttu-id="33d7c-139">Uma vez personalizado <xref:System.ServiceModel.ServiceAuthorizationManager> é implementada, o host de serviço deve ser informado sobre o <xref:System.ServiceModel.ServiceAuthorizationManager> para usar.</span><span class="sxs-lookup"><span data-stu-id="33d7c-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="33d7c-140">Isso é feito conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="33d7c-140">This is done as shown in the following code.</span></span>  
  
```xml  
<behavior ...>  
    ...  
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">  
        ...  
    </serviceAuthorization>  
</behavior>  
```  
  
 <span data-ttu-id="33d7c-141">O principal <xref:System.IdentityModel.Policy.IAuthorizationPolicy> para implementar o método é o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método.</span><span class="sxs-lookup"><span data-stu-id="33d7c-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>  
  
```  
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
  
 <span data-ttu-id="33d7c-142">Mostra o código anterior como o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> método verifica se nenhuma declaração foram adicionadas que afetam o processamento e adiciona declarações específicas.</span><span class="sxs-lookup"><span data-stu-id="33d7c-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="33d7c-143">As declarações que são permitidas são obtidas de `GetAllowedOpList` método, que é implementado para retornar uma lista específica de operações que o usuário tem permissão para executar.</span><span class="sxs-lookup"><span data-stu-id="33d7c-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="33d7c-144">A política de autorização adiciona declarações para acessar a operação específica.</span><span class="sxs-lookup"><span data-stu-id="33d7c-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="33d7c-145">Isso é usado posteriormente pelo <xref:System.ServiceModel.ServiceAuthorizationManager> para executar as decisões de seleção de acesso.</span><span class="sxs-lookup"><span data-stu-id="33d7c-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>  
  
 <span data-ttu-id="33d7c-146">Uma vez personalizado <xref:System.IdentityModel.Policy.IAuthorizationPolicy> é implementada, o host de serviço deve ser informado sobre as diretivas de autorização para usar.</span><span class="sxs-lookup"><span data-stu-id="33d7c-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>  
  
```xml  
<serviceAuthorization ...>  
       <authorizationPolicies>   
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />  
       </authorizationPolicies>   
</serviceAuthorization>  
```  
  
 <span data-ttu-id="33d7c-147">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="33d7c-148">O cliente chama a adicionar, subtrair e vários métodos e recebe uma mensagem de "Acesso negado" ao tentar chamar o método de divisão com êxito.</span><span class="sxs-lookup"><span data-stu-id="33d7c-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="33d7c-149">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-149">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="33d7c-150">Arquivo de lote</span><span class="sxs-lookup"><span data-stu-id="33d7c-150">Setup Batch File</span></span>  
 <span data-ttu-id="33d7c-151">Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo auto-hospedado que exige a segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>  
  
 <span data-ttu-id="33d7c-152">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="33d7c-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="33d7c-153">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-153">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="33d7c-154">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="33d7c-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="33d7c-155">A variável % SERVER_NAME % Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="33d7c-156">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="33d7c-157">O valor padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="33d7c-157">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="33d7c-158">Instalando o certificado de servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-158">Installing the server certificate into client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="33d7c-159">Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="33d7c-160">Esta etapa é necessária porque os certificados que são gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="33d7c-161">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="33d7c-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="33d7c-162">Criando o certificado de cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-162">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="33d7c-163">As seguintes linhas do arquivo em lotes bat criam o certificado de cliente a ser usado.</span><span class="sxs-lookup"><span data-stu-id="33d7c-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="33d7c-164">A variável % nome_do_usuário % Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="33d7c-165">Esse valor é definido como "test1" porque esse é o nome de `IAuthorizationPolicy` procura.</span><span class="sxs-lookup"><span data-stu-id="33d7c-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="33d7c-166">Se você alterar o valor de % username %, você deve alterar o valor correspondente no `IAuthorizationPolicy.Evaluate` método.</span><span class="sxs-lookup"><span data-stu-id="33d7c-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>  
  
     <span data-ttu-id="33d7c-167">O certificado é armazenado no repositório My (pessoal) no local de armazenamento CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="33d7c-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="33d7c-168">Instalando o certificado de cliente no repositório de certificados confiáveis do servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-168">Installing the client certificate into server's trusted certificate store.</span></span>  
  
     <span data-ttu-id="33d7c-169">As seguintes linhas no arquivo em lotes bat copie o certificado do cliente para o armazenamento de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="33d7c-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="33d7c-170">Esta etapa é necessária porque os certificados que são gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="33d7c-171">Se você já tiver um certificado que está enraizado em um certificado raiz confiável — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados do servidor com o certificado de cliente não é necessária.</span><span class="sxs-lookup"><span data-stu-id="33d7c-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="33d7c-172">Para configurar e criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="33d7c-172">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="33d7c-173">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33d7c-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="33d7c-174">Para executar o exemplo em uma configuração ou entre computadores, use as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="33d7c-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33d7c-175">Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="33d7c-176">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="33d7c-176">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="33d7c-177">Abra um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] janela de Prompt de comando com privilégios de administrador e execute bat da pasta de instalação do exemplo.</span><span class="sxs-lookup"><span data-stu-id="33d7c-177">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="33d7c-178">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="33d7c-178">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d7c-179">O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="33d7c-179">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="33d7c-180">Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.</span><span class="sxs-lookup"><span data-stu-id="33d7c-180">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="33d7c-181">Executar bat em um Visual Studio prompt de comando aberto com privilégios de administrador do exemplo de pasta de instalação.</span><span class="sxs-lookup"><span data-stu-id="33d7c-181">Run Setup.bat in a Visual Studio command prompt opened with administrator privileges from the sample install folder.</span></span> <span data-ttu-id="33d7c-182">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="33d7c-182">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="33d7c-183">Inicie Service.exe de service\bin.</span><span class="sxs-lookup"><span data-stu-id="33d7c-183">Launch Service.exe from service\bin.</span></span>  
  
4.  <span data-ttu-id="33d7c-184">Inicie Client.exe de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="33d7c-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="33d7c-185">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-185">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="33d7c-186">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="33d7c-186">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="33d7c-187">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="33d7c-187">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="33d7c-188">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="33d7c-188">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="33d7c-189">Copie os arquivos de programa do serviço de \service\bin para o diretório no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="33d7c-189">Copy the service program files from \service\bin to the directory on the service computer.</span></span> <span data-ttu-id="33d7c-190">Também copie os arquivos bat, Cleanup.bat, GetComputerName.vbs e ImportClientCert.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="33d7c-190">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="33d7c-191">Crie um diretório em que o cliente computerfor os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-191">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="33d7c-192">Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-192">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="33d7c-193">Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-193">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="33d7c-194">No servidor, execute `setup.bat service` em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="33d7c-194">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="33d7c-195">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computerand exporta o certificado de serviço em um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="33d7c-195">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="33d7c-196">Editar Service.exe.config para refletir o novo nome de certificado (no `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="33d7c-196">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="33d7c-197">Também alterar o nome do computador no \<serviço > /\<baseAddresses > elemento de localhost para o nome totalmente qualificado do computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="33d7c-197">Also change the computername in the \<service>/\<baseAddresses> element from localhost to the fully-qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="33d7c-198">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="33d7c-198">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="33d7c-199">No cliente, execute `setup.bat client` em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="33d7c-199">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="33d7c-200">Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado test1 e exporta o certificado de cliente para um arquivo chamado cer.</span><span class="sxs-lookup"><span data-stu-id="33d7c-200">Running `setup.bat` with the `client` argument creates a client certificate named test1 and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="33d7c-201">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="33d7c-201">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="33d7c-202">Faça isso substituindo localhost com o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-202">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="33d7c-203">Copie o arquivo CER do diretório do cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="33d7c-203">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="33d7c-204">No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="33d7c-204">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="33d7c-205">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="33d7c-205">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="33d7c-206">No servidor, execute ImportClientCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="33d7c-206">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="33d7c-207">Isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="33d7c-207">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="33d7c-208">No computador do servidor, inicie Service.exe da janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="33d7c-208">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="33d7c-209">No computador cliente, inicie o Client.exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="33d7c-209">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="33d7c-210">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="33d7c-210">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="33d7c-211">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="33d7c-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="33d7c-212">Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="33d7c-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="33d7c-213">Isso remove os certificados de servidor e cliente do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="33d7c-213">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33d7c-214">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="33d7c-214">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="33d7c-215">Se você tiver executado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos que usam certificados em computadores, certifique-se de desmarcar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="33d7c-215">If you have run [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="33d7c-216">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="33d7c-216">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d7c-217">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33d7c-217">See Also</span></span>
