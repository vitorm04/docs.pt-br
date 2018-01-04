---
title: Autenticador de token
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d635a1d5122319e228feb4d8a362b7609129c9de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="token-authenticator"></a><span data-ttu-id="ff8b3-102">Autenticador de token</span><span class="sxs-lookup"><span data-stu-id="ff8b3-102">Token Authenticator</span></span>
<span data-ttu-id="ff8b3-103">Este exemplo demonstra como implementar um autenticador de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="ff8b3-104">Um autenticador de token em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é usado para validar o token usado com a mensagem, verificar se ele é consistente e autenticar a identidade associada ao token.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-104">A token authenticator in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>  
  
 <span data-ttu-id="ff8b3-105">Autenticadores de token personalizados são úteis em uma variedade de casos, como:</span><span class="sxs-lookup"><span data-stu-id="ff8b3-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>  
  
-   <span data-ttu-id="ff8b3-106">Quando você deseja substituir o mecanismo de autenticação padrão associado a um token.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-106">When you want to override the default authentication mechanism associated with a token.</span></span>  
  
-   <span data-ttu-id="ff8b3-107">Quando você está criando um token personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-107">When you are building a custom token.</span></span>  
  
 <span data-ttu-id="ff8b3-108">Este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ff8b3-108">This sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="ff8b3-109">Como um cliente pode autenticar usando um par de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-109">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="ff8b3-110">Como o servidor pode validar as credenciais do cliente usando um autenticador de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-110">How the server can validate the client credentials using a custom token authenticator.</span></span>  
  
-   <span data-ttu-id="ff8b3-111">Como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] código de serviço está associado com o autenticador de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-111">How the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service code ties in with the custom token authenticator.</span></span>  
  
-   <span data-ttu-id="ff8b3-112">Como o servidor pode ser autenticado usando o certificado do servidor x. 509.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-112">How the server can be authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="ff8b3-113">Este exemplo também mostra como a identidade do chamador é acessível de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] após o processo de autenticação de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-113">This sample also shows how the caller's identity is accessible from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="ff8b3-114">O serviço expõe um ponto de extremidade de comunicação com o serviço, definido usando o arquivo de configuração App. config.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="ff8b3-115">O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ff8b3-116">A associação está configurada com um padrão `wsHttpBinding`, com o modo de segurança definido para a mensagem - o modo padrão da `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="ff8b3-117">Este exemplo define o padrão de `wsHttpBinding` para usar a autenticação de nome de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="ff8b3-118">O serviço também configura o certificado de serviço usando `serviceCredentials` comportamento.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="ff8b3-119">O `securityCredentials` comportamento permite que você especifique um certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="ff8b3-120">Um certificado de serviço é usado por um cliente para autenticar o serviço e fornecer proteção de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="ff8b3-121">A configuração a seguir faz referência ao certificado de localhost instalado durante a configuração de exemplo, conforme descrito nas instruções de instalação a seguir.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate.  
          A service certificate is used by a client to authenticate the service and provide message protection.  
          This configuration references the "localhost" certificate installed during the setup instructions.  
....        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="ff8b3-122">A configuração do ponto de extremidade cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="ff8b3-123">A ligação do cliente é configurado com as `Mode` e `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint name=""  
                address="http://localhost:8000/servicemodelsamples/service"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="ff8b3-124">A implementação de cliente define o nome de usuário e senha a ser usada.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-124">The client implementation sets the user name and password to use.</span></span>  
  
```  
static void Main()  
{  
     ...  
     client.ClientCredentials.UserNamePassword.UserName = username;  
     client.ClientCredentials.UserNamePassword.Password = password;  
     ...  
}  
```  
  
## <a name="custom-token-authenticator"></a><span data-ttu-id="ff8b3-125">Autenticador de Token personalizado</span><span class="sxs-lookup"><span data-stu-id="ff8b3-125">Custom Token Authenticator</span></span>  
 <span data-ttu-id="ff8b3-126">Use as etapas a seguir para criar um autenticador de token personalizado:</span><span class="sxs-lookup"><span data-stu-id="ff8b3-126">Use the following steps to create a custom token authenticator:</span></span>  
  
1.  <span data-ttu-id="ff8b3-127">Grave um autenticador de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-127">Write a custom token authenticator.</span></span>  
  
     <span data-ttu-id="ff8b3-128">O exemplo implementa um autenticador de token personalizado que valida o nome de usuário tem um formato de email válido.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="ff8b3-129">Ele é derivado de <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="ff8b3-130">O método mais importante dessa classe é <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="ff8b3-131">Nesse método, o autenticador valida o formato do nome de usuário e também que o nome do host não é de um domínio autorizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="ff8b3-132">Se ambas as condições forem atendidas, ele retorna uma coleção somente leitura de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instâncias que é usado para fornecer declarações que representam as informações armazenadas dentro do token de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>  
  
    ```  
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)  
    {  
        if (!ValidateUserNameFormat(userName))  
            throw new SecurityTokenValidationException("Incorrect UserName format");  
  
        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));  
        List<IIdentity> identities = new List<IIdentity>(1);  
        identities.Add(new GenericIdentity(userName));  
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);  
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));  
        return policies.AsReadOnly();  
    }  
    ```  
  
2.  <span data-ttu-id="ff8b3-133">Forneça uma diretiva de autorização que é retornada pelo autenticador de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>  
  
     <span data-ttu-id="ff8b3-134">Este exemplo fornece sua própria implementação de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> chamado `UnconditionalPolicy` que retorna o conjunto de declarações e as identidades que foram passadas para ele em seu construtor.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>  
  
    ```  
    class UnconditionalPolicy : IAuthorizationPolicy  
    {  
        String id = Guid.NewGuid().ToString();  
        ClaimSet issuer;  
        ClaimSet issuance;  
        DateTime expirationTime;  
        IList<IIdentity> identities;  
  
        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)  
        {  
            if (issuer == null)  
                throw new ArgumentNullException("issuer");  
            if (issuance == null)  
                throw new ArgumentNullException("issuance");  
  
            this.issuer = issuer;  
            this.issuance = issuance;  
            this.identities = identities;  
            this.expirationTime = expirationTime;  
        }  
  
        public string Id  
        {  
            get { return this.id; }  
        }  
  
        public ClaimSet Issuer  
        {  
            get { return this.issuer; }  
        }  
  
        public DateTime ExpirationTime  
        {  
            get { return this.expirationTime; }  
        }  
  
        public bool Evaluate(EvaluationContext evaluationContext, ref object state)  
        {  
            evaluationContext.AddToTarget(this, this.issuance);  
  
            if (this.identities != null)  
            {  
                object value;  
                IList<IIdentity> contextIdentities;  
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))  
                {  
                    contextIdentities = new List<IIdentity>(this.identities.Count);  
                    evaluationContext.Properties.Add("Identities", contextIdentities);  
                }  
                else  
                {  
                    contextIdentities = value as IList<IIdentity>;  
                }  
                foreach (IIdentity identity in this.identities)  
                {  
                    contextIdentities.Add(identity);  
                }  
            }  
  
            evaluationContext.RecordExpirationTime(this.expirationTime);  
            return true;  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="ff8b3-135">Grave um Gerenciador de token de segurança personalizada.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-135">Write a custom security token manager.</span></span>  
  
     <span data-ttu-id="ff8b3-136">O <xref:System.IdentityModel.Selectors.SecurityTokenManager> é usado para criar um <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> para determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objetos que são passados para ele no `CreateSecurityTokenAuthenticator` método.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="ff8b3-137">O Gerenciador de token de segurança também é usado para criar provedores de token e serializadores de token, mas aqueles não são cobertas por este exemplo.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="ff8b3-138">Neste exemplo, o Gerenciador de token de segurança personalizada herda de <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> classe e substituições de `CreateSecurityTokenAuthenticator` método para retornar o autenticador de token de nome de usuário personalizada quando os requisitos de token passados indicam que autenticador de nome de usuário é solicitado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>  
  
    ```  
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager  
    {  
        MyUserNameCredential myUserNameCredential;  
  
        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)  
            : base(myUserNameCredential)  
        {  
            this.myUserNameCredential = myUserNameCredential;  
        }  
  
        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)  
        {  
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)  
            {  
                outOfBandTokenResolver = null;  
                return new MyTokenAuthenticator();  
            }  
            else  
            {  
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="ff8b3-139">Grave uma credencial de serviço personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-139">Write a custom service credential.</span></span>  
  
     <span data-ttu-id="ff8b3-140">A classe de credenciais de serviço é usada para representar as credenciais que são configuradas para o serviço e cria o Gerenciador de token que é usado para obter autenticadores de token, provedores de token e serializadores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```  
    public class MyUserNameCredential : ServiceCredentials  
    {  
  
        public MyUserNameCredential()  
            : base()  
        {  
        }  
  
        protected override ServiceCredentials CloneCore()  
        {  
            return new MyUserNameCredential();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new MySecurityTokenManager(this);  
        }  
  
    }  
    ```  
  
5.  <span data-ttu-id="ff8b3-141">Configure o serviço para usar a credencial de serviço personalizado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-141">Configure the service to use the custom service credential.</span></span>  
  
     <span data-ttu-id="ff8b3-142">Em ordem para o serviço para usar a credencial de serviço personalizado, podemos excluir a classe de credencial de serviço padrão depois de capturar o certificado de serviço já está pré-configurado na credencial de serviço padrão e configurar a nova credencial de serviço instância para usar os certificados de serviço pré-configurado e adicionar essa nova instância de credencial de serviço a comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 <span data-ttu-id="ff8b3-143">Para exibir informações do chamador, você pode usar o <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="ff8b3-144">O <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contém informações de declarações sobre o chamador atual.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 <span data-ttu-id="ff8b3-145">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ff8b3-146">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-146">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="ff8b3-147">Arquivo de lote</span><span class="sxs-lookup"><span data-stu-id="ff8b3-147">Setup Batch File</span></span>  
 <span data-ttu-id="ff8b3-148">Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer um servidor de segurança baseada em certificado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="ff8b3-149">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="ff8b3-150">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>  
  
-   <span data-ttu-id="ff8b3-151">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-151">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="ff8b3-152">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="ff8b3-153">O `%SERVER_NAME%` variável Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="ff8b3-154">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ff8b3-155">O padrão, esse arquivo em lotes é localhost.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-155">The default in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="ff8b3-156">Instalando o certificado de servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-156">Installing the server certificate into client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="ff8b3-157">Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ff8b3-158">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ff8b3-159">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ff8b3-160">O arquivo de lote é projetado para ser executado de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="ff8b3-161">Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="ff8b3-162">Essa variável de ambiente é definida automaticamente em um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="ff8b3-163">Para configurar e criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ff8b3-163">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="ff8b3-164">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff8b3-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ff8b3-165">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff8b3-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ff8b3-166">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="ff8b3-166">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="ff8b3-167">Execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-167">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="ff8b3-168">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-168">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ff8b3-169">O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-169">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="ff8b3-170">Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-170">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="ff8b3-171">Inicie service.exe de service\bin.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-171">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="ff8b3-172">Inicie client.exe de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="ff8b3-173">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-173">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="ff8b3-174">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ff8b3-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ff8b3-175">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="ff8b3-175">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="ff8b3-176">Crie um diretório no computador de serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="ff8b3-177">Copie os arquivos de programa do serviço para o diretório de serviço no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="ff8b3-178">Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="ff8b3-179">Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="ff8b3-180">O arquivo App. config do serviço deve ser atualizado para refletir o novo nome de certificado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="ff8b3-181">Você pode criar uma usando o bat se você definir o `%SERVER_NAME%` variável ao nome de host totalmente qualificado do computador no qual o serviço será executado.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="ff8b3-182">Observe que o arquivo bat deve ser executado em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-182">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="ff8b3-183">Copie o certificado do servidor para o armazenamento CurrentUser TrustedPeople do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="ff8b3-184">Você não precisa fazer isso, exceto quando o certificado do servidor é emitido por um emissor confiável do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="ff8b3-185">No arquivo App. config no computador de serviço, altere o valor do endereço base para especificar um nome de computador totalmente qualificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="ff8b3-186">No computador do serviço, execute service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="ff8b3-187">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="ff8b3-188">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="ff8b3-189">No computador cliente, inicie o Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="ff8b3-190">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ff8b3-190">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ff8b3-191">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="ff8b3-191">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="ff8b3-192">Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="ff8b3-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8b3-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff8b3-193">See Also</span></span>
