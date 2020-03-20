---
title: Serviço de fachada confiável
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 17901b7a68d4701287d02bc7ee3174683e777fd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143740"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="b6aa2-102">Serviço de fachada confiável</span><span class="sxs-lookup"><span data-stu-id="b6aa2-102">Trusted Facade Service</span></span>
<span data-ttu-id="b6aa2-103">Esta amostra de cenário demonstra como fluir as informações de identidade do chamador de um serviço para outro usando a infra-estrutura de segurança da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b6aa2-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="b6aa2-104">É um padrão de design comum para expor a funcionalidade fornecida por um serviço à rede pública usando um serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="b6aa2-105">O serviço de fachada normalmente reside na rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede rastreada) e se comunica com um serviço de back-end que implementa a lógica de negócios e tem acesso a dados internos.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="b6aa2-106">O canal de comunicação entre o serviço de fachada e o serviço de back-end passa por um firewall e geralmente é limitado apenas para um único propósito.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="b6aa2-107">Esta amostra consiste nos seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="b6aa2-107">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="b6aa2-108">Cliente da calculadora</span><span class="sxs-lookup"><span data-stu-id="b6aa2-108">Calculator client</span></span>  
  
- <span data-ttu-id="b6aa2-109">Serviço de fachada de calculadora</span><span class="sxs-lookup"><span data-stu-id="b6aa2-109">Calculator façade service</span></span>  
  
- <span data-ttu-id="b6aa2-110">Serviço de backend da calculadora</span><span class="sxs-lookup"><span data-stu-id="b6aa2-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="b6aa2-111">O serviço de fachada é responsável por validar a solicitação e autenticar o chamador.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="b6aa2-112">Após autenticação e validação bem-sucedidas, ele encaminha a solicitação para o serviço backend usando o canal de comunicação controlado da rede de perímetro para a rede interna.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="b6aa2-113">Como parte da solicitação encaminhada, o serviço de fachada inclui informações sobre a identidade do chamador para que o serviço de back-end possa usar essas informações em seu processamento.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="b6aa2-114">A identidade do chamador é `Username` transmitida usando um `Security` token de segurança dentro do cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="b6aa2-115">A amostra usa a infra-estrutura de segurança `Security` WCF para transmitir e extrair essas informações do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b6aa2-116">O serviço backend confia no serviço de fachada para autenticar o chamador.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="b6aa2-117">Por causa disso, o serviço backend não autentica o chamador novamente; utiliza as informações de identidade fornecidas pelo serviço de fachada na solicitação encaminhada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="b6aa2-118">Por causa dessa relação de confiança, o serviço de back-end deve autenticar o serviço de fachada para garantir que a mensagem encaminhada venha de uma fonte confiável - neste caso, o serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="b6aa2-119">Implementação</span><span class="sxs-lookup"><span data-stu-id="b6aa2-119">Implementation</span></span>  
 <span data-ttu-id="b6aa2-120">Há dois caminhos de comunicação nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="b6aa2-121">Primeiro é entre o cliente e o serviço de fachada, o segundo é entre o serviço de fachada e o serviço back-end.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="b6aa2-122">Caminho de Comunicação entre Cliente e Serviço de Fachada</span><span class="sxs-lookup"><span data-stu-id="b6aa2-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="b6aa2-123">O cliente para o caminho `wsHttpBinding` de `UserName` comunicação de serviço de fachada usa com um tipo de credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="b6aa2-124">Isso significa que o cliente usa nome de usuário e senha para autenticar ao serviço de fachada e o serviço de fachada usa o certificado X.509 para autenticar ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="b6aa2-125">A configuração de vinculação parece ser o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="b6aa2-126">O serviço de fachada autentica o `UserNamePasswordValidator` chamador usando a implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="b6aa2-127">Para fins de demonstração, a autenticação apenas garante que o nome de usuário do chamador corresponda à senha apresentada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="b6aa2-128">Na situação do mundo real, o usuário provavelmente é autenticado usando o Active Directory ou o provedor de associação de ASP.NET personalizado.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="b6aa2-129">A implementação do `FacadeService.cs` validador reside no arquivo.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b6aa2-130">O validador personalizado está configurado `serviceCredentials` para ser usado dentro do comportamento no arquivo de configuração do serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="b6aa2-131">Esse comportamento também é usado para configurar o certificado X.509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="b6aa2-132">Caminho de comunicação entre serviço de fachada e serviço backend</span><span class="sxs-lookup"><span data-stu-id="b6aa2-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="b6aa2-133">O serviço de fachada para o caminho `customBinding` de comunicação de serviço back-end utiliza um que consiste em vários elementos de ligação.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="b6aa2-134">Essa ligação realiza duas coisas.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-134">This binding accomplishes two things.</span></span> <span data-ttu-id="b6aa2-135">Ele autentica o serviço de fachada e o serviço de backend para garantir que a comunicação seja segura e venha de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="b6aa2-136">Além disso, ele também transmite a identidade `Username` do chamador inicial dentro do token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="b6aa2-137">Neste caso, apenas o nome de usuário do chamador inicial é transmitido para o serviço de back-end, a senha não está incluída na mensagem.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="b6aa2-138">Isso porque o serviço backend confia no serviço de fachada para autenticar o chamador antes de encaminhar a solicitação para ele.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="b6aa2-139">Como o serviço de fachada se autentica no serviço backend, o serviço de back-end pode confiar nas informações contidas na solicitação encaminhada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="b6aa2-140">A seguir está a configuração de vinculação para este caminho de comunicação.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="b6aa2-141">O elemento [ \<de ligação de segurança>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) cuida da transmissão e extração do nome de usuário do chamador inicial.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="b6aa2-142">O [ \<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) e [ \<o tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cuidar da autenticação dos serviços de fachada e back-end e proteção de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="b6aa2-143">Para encaminhar a solicitação, a implementação do serviço de fachada deve fornecer o nome de usuário do chamador inicial para que a infra-estrutura de segurança do WCF possa colocá-la na mensagem encaminhada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="b6aa2-144">O nome de usuário do chamador inicial é fornecido na `ClientCredentials` implementação do serviço de fachada, definindo-o na propriedade na instância de proxy do cliente que o serviço de fachada usa para se comunicar com o serviço backend.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="b6aa2-145">O código a `GetCallerIdentity` seguir mostra como o método é implementado no serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="b6aa2-146">Outros métodos usam o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-146">Other methods use the same pattern.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="b6aa2-147">Como mostrado no código anterior, a senha `ClientCredentials` não está definida na propriedade, apenas o nome de usuário é definido.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="b6aa2-148">A infra-estrutura de segurança WCF cria um token de segurança de nome de usuário sem senha neste caso, que é exatamente o que é necessário neste cenário.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="b6aa2-149">No serviço backend, as informações contidas no token de segurança do nome de usuário devem ser autenticadas.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="b6aa2-150">Por padrão, a segurança do WCF tenta mapear o usuário para uma conta do Windows usando a senha fornecida.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="b6aa2-151">Neste caso, não há senha fornecida e o serviço de back-end não é necessário para autenticar o nome de usuário porque a autenticação já foi realizada pelo serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="b6aa2-152">Para implementar essa funcionalidade no WCF, é fornecido um personalizado `UserNamePasswordValidator` que apenas impõe que um nome de usuário seja especificado no token e não execute nenhuma autenticação adicional.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b6aa2-153">O validador personalizado está configurado `serviceCredentials` para ser usado dentro do comportamento no arquivo de configuração do serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="b6aa2-154">Para extrair as informações e informações sobre o nome de usuário e `ServiceSecurityContext` informações sobre a conta de serviço de fachada confiável, a implementação do serviço backend usa a classe.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="b6aa2-155">O código a `GetCallerIdentity` seguir mostra como o método é implementado.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="b6aa2-156">As informações da conta de serviço `ServiceSecurityContext.Current.WindowsIdentity` de fachada são extraídas usando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="b6aa2-157">Para acessar as informações sobre o chamador `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` inicial, o serviço backend usa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="b6aa2-158">Ele procura `Identity` uma reivindicação `Name`com um tipo.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="b6aa2-159">Essa reclamação é gerada automaticamente pela infra-estrutura de `Username` segurança WCF a partir das informações contidas no token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="b6aa2-160">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="b6aa2-160">Running the sample</span></span>  
 <span data-ttu-id="b6aa2-161">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b6aa2-162">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="b6aa2-163">Você pode pressionar ENTER nas janelas do console de serviço de fachada e back-end para desligar os serviços.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```console  
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
  
 <span data-ttu-id="b6aa2-164">O arquivo de lote Setup.bat incluído na amostra de cenário Trusted Facade permite configurar o servidor com um certificado relevante para executar o serviço de fachada que requer segurança baseada em certificado para autenticar-se ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="b6aa2-165">Consulte o procedimento de configuração no final deste tópico para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="b6aa2-166">O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="b6aa2-167">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="b6aa2-168">As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="b6aa2-169">A `%SERVER_NAME%` variável especifica o nome do servidor - o valor padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="b6aa2-170">O certificado é armazenado na loja LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-170">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="b6aa2-171">Instalando o certificado do serviço de fachada na loja de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="b6aa2-172">A linha a seguir copia o certificado do serviço de fachada na loja de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="b6aa2-173">Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="b6aa2-174">Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b6aa2-175">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b6aa2-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b6aa2-176">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b6aa2-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b6aa2-177">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b6aa2-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="b6aa2-178">Para executar a amostra na mesma máquina</span><span class="sxs-lookup"><span data-stu-id="b6aa2-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="b6aa2-179">Certifique-se de que o caminho inclui a pasta onde o Makecert.exe está localizado.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="b6aa2-180">Executar Setup.bat da pasta de instalação de amostra.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="b6aa2-181">Isso instala todos os certificados necessários para a execução da amostra.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="b6aa2-182">Inicie o BackendService.exe do diretório \BackendService\bin em uma janela de console separada</span><span class="sxs-lookup"><span data-stu-id="b6aa2-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="b6aa2-183">Inicie o Diretório FacadeService.exe de \FacadeService\bin em uma janela de console separada</span><span class="sxs-lookup"><span data-stu-id="b6aa2-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="b6aa2-184">Inicie client.exe a partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="b6aa2-185">A atividade do cliente é exibida no aplicativo do console cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="b6aa2-186">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="b6aa2-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="b6aa2-187">Para limpar depois da amostra</span><span class="sxs-lookup"><span data-stu-id="b6aa2-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="b6aa2-188">Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b6aa2-189">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b6aa2-190">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-190">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b6aa2-191">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="b6aa2-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b6aa2-192">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b6aa2-192">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
