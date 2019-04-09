---
title: Serviço de fachada confiável
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 4b02928224f1cb96a25dc71941273625e7d9e5e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091545"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="ece5d-102">Serviço de fachada confiável</span><span class="sxs-lookup"><span data-stu-id="ece5d-102">Trusted Facade Service</span></span>
<span data-ttu-id="ece5d-103">Este exemplo de cenário demonstra como fluxo de informações de identidade do chamador de um serviço para outro usando o Windows Communication Foundation (WCF) infraestrutura de segurança.</span><span class="sxs-lookup"><span data-stu-id="ece5d-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="ece5d-104">É um padrão de design comum para expor a funcionalidade fornecida por um serviço para a rede pública usando um serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="ece5d-105">Normalmente, o serviço de fachada reside na rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede filtrada) e se comunica com um serviço de back-end que implementa a lógica de negócios e tem acesso aos dados internos.</span><span class="sxs-lookup"><span data-stu-id="ece5d-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="ece5d-106">O canal de comunicação entre o serviço de fachada e o serviço de back-end passa por um firewall e geralmente é limitado para somente uma única finalidade.</span><span class="sxs-lookup"><span data-stu-id="ece5d-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="ece5d-107">Esse exemplo consiste nos seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="ece5d-107">This sample consists of the following components:</span></span>  
  
-   <span data-ttu-id="ece5d-108">Cliente de Calculadora</span><span class="sxs-lookup"><span data-stu-id="ece5d-108">Calculator client</span></span>  
  
-   <span data-ttu-id="ece5d-109">Serviço de fachada de Calculadora</span><span class="sxs-lookup"><span data-stu-id="ece5d-109">Calculator façade service</span></span>  
  
-   <span data-ttu-id="ece5d-110">Serviço de back-end de Calculadora</span><span class="sxs-lookup"><span data-stu-id="ece5d-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="ece5d-111">O serviço de fachada é responsável por validar a solicitação e autenticar o chamador.</span><span class="sxs-lookup"><span data-stu-id="ece5d-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="ece5d-112">Após a autenticação e validação, ele encaminha a solicitação para o serviço de back-end usando o canal de comunicação controlada da rede de perímetro para a rede interna.</span><span class="sxs-lookup"><span data-stu-id="ece5d-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="ece5d-113">Como parte da solicitação encaminhada, o serviço de fachada inclui informações sobre a identidade do chamador para que o serviço de back-end pode usar essas informações no seu processamento.</span><span class="sxs-lookup"><span data-stu-id="ece5d-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="ece5d-114">A identidade do chamador é transmitida usando um `Username` token de segurança dentro da mensagem `Security` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="ece5d-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="ece5d-115">O exemplo usa a infraestrutura de segurança do WCF para transmitir e extrair essas informações do `Security` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="ece5d-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ece5d-116">O serviço de back-end confia que o serviço de fachada para autenticar o chamador.</span><span class="sxs-lookup"><span data-stu-id="ece5d-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="ece5d-117">Por isso, o serviço de back-end não autentica o chamador novamente; Ele usa as informações de identidade fornecidas pelo serviço de fachada na solicitação encaminhada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="ece5d-118">Devido a essa relação de confiança, o serviço de back-end deve autenticar o serviço de fachada para garantir que a mensagem encaminhada vem de uma fonte confiável - nesse caso, o serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="ece5d-119">Implementação</span><span class="sxs-lookup"><span data-stu-id="ece5d-119">Implementation</span></span>  
 <span data-ttu-id="ece5d-120">Há dois caminhos de comunicação neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="ece5d-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="ece5d-121">Primeiro é entre o cliente e o serviço de fachada, a segunda é entre o serviço de fachada e o serviço de back-end.</span><span class="sxs-lookup"><span data-stu-id="ece5d-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="ece5d-122">Caminho de comunicação entre cliente e serviço de fachada</span><span class="sxs-lookup"><span data-stu-id="ece5d-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="ece5d-123">Usa o cliente para o caminho de comunicação do serviço de fachada `wsHttpBinding` com um `UserName` tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="ece5d-124">Isso significa que o cliente usa o nome de usuário e senha para autenticar para o serviço de fachada e o serviço de fachada usa o certificado x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="ece5d-125">A configuração de associação é semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ece5d-125">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="ece5d-126">O serviço de fachada autentica o chamador usar custom `UserNamePasswordValidator` implementação.</span><span class="sxs-lookup"><span data-stu-id="ece5d-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="ece5d-127">Para fins de demonstração, a autenticação apenas garante que o nome de usuário do chamador corresponde à senha apresentada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="ece5d-128">A situação de mundo real, o usuário provavelmente é autenticado usando o Active Directory ou o provedor de associação do ASP.NET personalizado.</span><span class="sxs-lookup"><span data-stu-id="ece5d-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="ece5d-129">A implementação de validador reside no `FacadeService.cs` arquivo.</span><span class="sxs-lookup"><span data-stu-id="ece5d-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ece5d-130">O validador personalizado está configurado para ser usado dentro de `serviceCredentials` comportamento no arquivo de configuração de serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="ece5d-131">Esse comportamento também é usado para configurar o certificado do serviço x. 509.</span><span class="sxs-lookup"><span data-stu-id="ece5d-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate   
               findValue="localhost"   
               storeLocation="LocalMachine"   
               storeName="My"   
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="ece5d-132">Caminho de comunicação entre o serviço de fachada e serviço de back-end</span><span class="sxs-lookup"><span data-stu-id="ece5d-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="ece5d-133">O serviço de fachada para o caminho de comunicação do serviço de back-end usa um `customBinding` que consiste em vários elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="ece5d-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="ece5d-134">Essa associação faz duas coisas:</span><span class="sxs-lookup"><span data-stu-id="ece5d-134">This binding accomplishes two things.</span></span> <span data-ttu-id="ece5d-135">Ele autentica o serviço de fachada e o serviço de back-end para garantir que a comunicação seja segura e é proveniente de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="ece5d-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="ece5d-136">Além disso, ele também transmite a identidade do chamador inicial dentro de `Username` token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ece5d-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="ece5d-137">Nesse caso, somente nome de usuário do chamador inicial é transmitida para o serviço de back-end, a senha não está incluída na mensagem.</span><span class="sxs-lookup"><span data-stu-id="ece5d-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="ece5d-138">Isso ocorre porque o serviço de fachada para autenticar o chamador antes de encaminhar a solicitação para ele de relações de confiança do serviço de back-end.</span><span class="sxs-lookup"><span data-stu-id="ece5d-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="ece5d-139">Porque o serviço de fachada se autentica para o serviço de back-end, o serviço de back-end pode confiar as informações contidas na solicitação encaminhada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="ece5d-140">A seguir está a configuração de associação para este caminho de comunicação.</span><span class="sxs-lookup"><span data-stu-id="ece5d-140">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="ece5d-141">O [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento de associação se encarrega de transmissão de nome de usuário e a extração do chamador inicial.</span><span class="sxs-lookup"><span data-stu-id="ece5d-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="ece5d-142">O [ \<windowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) e [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cuidar da autenticação dos serviços de fachada e de back-end e a proteção da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ece5d-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="ece5d-143">Para encaminhar a solicitação, a implementação do serviço de fachada deve fornecer o nome de usuário do chamador inicial para que essa infraestrutura de segurança do WCF pode colocá-la para a mensagem encaminhada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="ece5d-144">Nome de usuário do chamador inicial é fornecido na implementação do serviço de fachada definindo-o `ClientCredentials` desse serviço de fachada de propriedade na instância do proxy do cliente usa para se comunicar com o serviço de back-end.</span><span class="sxs-lookup"><span data-stu-id="ece5d-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="ece5d-145">O seguinte código mostra como `GetCallerIdentity` método é implementado no serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="ece5d-146">Outros métodos usem o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="ece5d-146">Other methods use the same pattern.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="ece5d-147">Conforme mostrado no código anterior, a senha não está definida no `ClientCredentials` , somente o nome de usuário estiver definida.</span><span class="sxs-lookup"><span data-stu-id="ece5d-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="ece5d-148">Infraestrutura de segurança do WCF cria um token de segurança do nome de usuário sem uma senha nesse caso, o que é exatamente o que é necessária nesse cenário.</span><span class="sxs-lookup"><span data-stu-id="ece5d-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="ece5d-149">No serviço de back-end, as informações contidas no token de segurança de nome de usuário devem ser autenticadas.</span><span class="sxs-lookup"><span data-stu-id="ece5d-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="ece5d-150">Por padrão, a segurança do WCF tenta mapear o usuário a uma conta do Windows usando a senha fornecida.</span><span class="sxs-lookup"><span data-stu-id="ece5d-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="ece5d-151">Nesse caso, não há nenhuma senha fornecida e o serviço de back-end não é necessária para autenticar o nome de usuário porque a autenticação já foi executada pelo serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="ece5d-152">Para implementar essa funcionalidade no WCF, um personalizado `UserNamePasswordValidator` for fornecido, que impõe apenas que um nome de usuário é especificada no token e não executa nenhuma autenticação adicional.</span><span class="sxs-lookup"><span data-stu-id="ece5d-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,   
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the   
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new   
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ece5d-153">O validador personalizado está configurado para ser usado dentro de `serviceCredentials` comportamento no arquivo de configuração de serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="ece5d-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,   
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="ece5d-154">Para extrair as informações de nome de usuário e informações sobre a conta de serviço de fachada confiável, a implementação do serviço de back-end usa o `ServiceSecurityContext` classe.</span><span class="sxs-lookup"><span data-stu-id="ece5d-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="ece5d-155">O seguinte código mostra como o `GetCallerIdentity` método é implementado.</span><span class="sxs-lookup"><span data-stu-id="ece5d-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =   
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on   
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in   
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets   
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in   
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&   
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject   
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="ece5d-156">As informações de conta de serviço de fachada são extraídas usando o `ServiceSecurityContext.Current.WindowsIdentity` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ece5d-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="ece5d-157">Para acessar as informações sobre o chamador inicial o serviço de back-end usa o `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ece5d-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="ece5d-158">Ele procura por um `Identity` com um tipo de declaração `Name`.</span><span class="sxs-lookup"><span data-stu-id="ece5d-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="ece5d-159">Essa declaração é gerada automaticamente pela infraestrutura de segurança do WCF das informações contidas no `Username` token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ece5d-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="ece5d-160">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="ece5d-160">Running the sample</span></span>  
 <span data-ttu-id="ece5d-161">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ece5d-162">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="ece5d-163">Você pode pressionar ENTER nas janelas do console de serviço fachada e de back-end para desligar os serviços.</span><span class="sxs-lookup"><span data-stu-id="ece5d-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ece5d-164">O arquivo em lotes de Setup. bat incluído no exemplo de cenário de fachada confiável permite que você configure o servidor com um certificado apropriado para executar o serviço de fachada que exija segurança baseada em certificado para autenticar-se com o cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="ece5d-165">Consulte o procedimento de instalação no final deste tópico para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="ece5d-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="ece5d-166">O exemplo a seguir fornece uma visão geral sobre as diferentes seções dos arquivos de lote.</span><span class="sxs-lookup"><span data-stu-id="ece5d-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="ece5d-167">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="ece5d-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="ece5d-168">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ece5d-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="ece5d-169">O `%SERVER_NAME%` variável Especifica o nome do servidor, o valor padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="ece5d-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="ece5d-170">O certificado é armazenado no repositório de LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ece5d-170">The certificate is stored in the LocalMachine store.</span></span>  
  
-   <span data-ttu-id="ece5d-171">Instalando o certificado do serviço de fachada no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="ece5d-172">A linha a seguir copia o certificado do serviço de fachada para o repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="ece5d-173">Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ece5d-174">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="ece5d-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ece5d-175">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ece5d-175">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ece5d-176">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ece5d-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ece5d-177">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ece5d-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="ece5d-178">Para executar o exemplo na mesma máquina</span><span class="sxs-lookup"><span data-stu-id="ece5d-178">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="ece5d-179">Certifique-se de que o caminho inclui a pasta onde se encontra Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="ece5d-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="ece5d-180">Execute Setup. bat da pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ece5d-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="ece5d-181">Essa opção instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ece5d-181">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="ece5d-182">Inicie o BackendService.exe do diretório \BackendService\bin em uma janela separada do console</span><span class="sxs-lookup"><span data-stu-id="ece5d-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4.  <span data-ttu-id="ece5d-183">Inicie o FacadeService.exe do diretório \FacadeService\bin em uma janela separada do console</span><span class="sxs-lookup"><span data-stu-id="ece5d-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5.  <span data-ttu-id="ece5d-184">Inicie o Client.exe no \client\bin.</span><span class="sxs-lookup"><span data-stu-id="ece5d-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ece5d-185">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ece5d-185">Client activity is displayed on the client console application.</span></span>  
  
6.  <span data-ttu-id="ece5d-186">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ece5d-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ece5d-187">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="ece5d-187">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="ece5d-188">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="ece5d-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ece5d-189">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ece5d-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ece5d-190">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ece5d-190">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ece5d-191">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ece5d-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ece5d-192">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ece5d-192">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
