---
title: Provedor de tokens emitidos duráveis
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: bfe8f8bb8c3775760bc69031e338a156d690ab25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487596"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="90121-102">Provedor de tokens emitidos duráveis</span><span class="sxs-lookup"><span data-stu-id="90121-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="90121-103">Este exemplo demonstra como implementar uma provedor de token emitida personalizadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="90121-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="90121-104">Discussão</span><span class="sxs-lookup"><span data-stu-id="90121-104">Discussion</span></span>  
 <span data-ttu-id="90121-105">Um provedor de token no Windows Communication Foundation (WCF) é usado para fornecer credenciais para a infraestrutura de segurança.</span><span class="sxs-lookup"><span data-stu-id="90121-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="90121-106">O provedor de token em geral examina o destino e problemas apropriado as credenciais para que a infraestrutura de segurança pode proteger a mensagem.</span><span class="sxs-lookup"><span data-stu-id="90121-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="90121-107">O WCF é fornecido com um provedor de token do CardSpace.</span><span class="sxs-lookup"><span data-stu-id="90121-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="90121-108">Provedores de token personalizados são úteis nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="90121-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="90121-109">Se você tiver um repositório de credenciais que o provedor de token interno não pode operar com.</span><span class="sxs-lookup"><span data-stu-id="90121-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="90121-110">Se você quiser fornecer seu próprio mecanismo personalizado para transformar as credenciais do ponto quando o usuário fornece os detalhes para quando o cliente WCF usa as credenciais.</span><span class="sxs-lookup"><span data-stu-id="90121-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="90121-111">Se você estiver criando um token personalizado.</span><span class="sxs-lookup"><span data-stu-id="90121-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="90121-112">Este exemplo mostra como criar um provedor de token personalizado que armazena em cache os tokens emitidos por um Security Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="90121-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="90121-113">Para resumir, este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="90121-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="90121-114">Como um cliente pode ser configurado com um provedor de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="90121-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="90121-115">Como os tokens emitidos podem ser armazenados em cache e fornecidos para o cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="90121-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="90121-116">Como o servidor é autenticado pelo cliente usando o certificado do servidor x. 509.</span><span class="sxs-lookup"><span data-stu-id="90121-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="90121-117">Esse exemplo consiste em um programa de console de cliente (Client.exe), um programa de console do serviço de token de segurança (Securitytokenservice.exe) e um programa de console de serviço (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="90121-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="90121-118">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="90121-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="90121-119">O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="90121-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="90121-120">O cliente obtém uma token de segurança do Security Token Service (STS) e faz solicitações síncronas para o serviço para uma operação matemática determinado e as respostas de serviço com o resultado.</span><span class="sxs-lookup"><span data-stu-id="90121-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="90121-121">Atividade do cliente está visível na janela do console.</span><span class="sxs-lookup"><span data-stu-id="90121-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90121-122">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="90121-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="90121-123">Este exemplo expõe o contrato de ICalculator usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="90121-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="90121-124">A configuração desta associação no cliente é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="90121-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows" 
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="90121-125">Sobre o `security` elemento de `wsFederationHttpBinding`, o `mode` valor configura o modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="90121-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="90121-126">Neste exemplo, segurança de mensagens está sendo usada, que é por isso que o `message` elemento da `wsFederationHttpBinding` especificado dentro de `security` elemento da `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="90121-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="90121-127">O `issuer` elemento de `wsFederationHttpBinding` dentro de `message` elemento da `wsFederationHttpBinding` Especifica o endereço e a associação para o serviço de Token de segurança que emite um token de segurança para o cliente para que o cliente pode autenticar para a Calculadora serviço.</span><span class="sxs-lookup"><span data-stu-id="90121-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="90121-128">A configuração desta associação de serviço é mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="90121-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser" 
                                    storeName="TrustedPeople" 
                                    x509FindType="FindBySubjectDistinguishedName" 
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="90121-129">Sobre o `security` elemento de `wsFederationHttpBinding`, o `mode` valor configura o modo de segurança deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="90121-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="90121-130">Neste exemplo, segurança de mensagens está sendo usada, que é por isso que o `message` elemento da `wsFederationHttpBinding` especificado dentro de `security` elemento da `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="90121-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="90121-131">O `issuerMetadata` elemento de `wsFederationHttpBinding` dentro de `message` elemento do `wsFederationHttpBinding` Especifica o endereço e a identidade para um ponto de extremidade que pode ser usado para recuperar metadados para o serviço de Token de segurança.</span><span class="sxs-lookup"><span data-stu-id="90121-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="90121-132">O comportamento para o serviço é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="90121-132">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine" 
              storeName="TrustedPeople" 
              x509FindType="FindBySubjectDistinguishedName" 
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine" 
                        storeName="My" 
                        x509FindType="FindBySubjectDistinguishedName" 
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 <span data-ttu-id="90121-133">O `issuedTokenAuthentication` elemento dentro do `serviceCredentials` elemento permite que o serviço especificar restrições nos tokens que ele permite que os clientes presentes durante a autenticação.</span><span class="sxs-lookup"><span data-stu-id="90121-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="90121-134">Essa configuração especifica que os tokens assinados por um certificado cujo nome de assunto é CN = STS são aceitos pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="90121-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="90121-135">O serviço de Token de segurança expõe um ponto de extremidade usando o wsHttpBinding padrão.</span><span class="sxs-lookup"><span data-stu-id="90121-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="90121-136">O serviço de Token de segurança responde à solicitação de clientes para tokens e, desde que o cliente é autenticado usando uma conta do Windows, emite um token que contém o nome de usuário do cliente como uma declaração no token emitido.</span><span class="sxs-lookup"><span data-stu-id="90121-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="90121-137">Como parte da criação de token, os sinais de serviço de Token de segurança o token usando a chave privada associada com o CN = certificado STS.</span><span class="sxs-lookup"><span data-stu-id="90121-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="90121-138">Além disso, ele cria uma chave simétrica e criptografa usando a chave pública associada com o CN = localhost certificate.</span><span class="sxs-lookup"><span data-stu-id="90121-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="90121-139">Retornar o token para o cliente, o serviço de Token de segurança também retorna a chave simétrica.</span><span class="sxs-lookup"><span data-stu-id="90121-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="90121-140">O cliente apresenta o token emitido para o serviço da Calculadora e comprova que ele saiba a chave simétrica inscrevendo-se a mensagem com essa chave.</span><span class="sxs-lookup"><span data-stu-id="90121-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="90121-141">Credenciais personalizadas do cliente e o provedor de Token</span><span class="sxs-lookup"><span data-stu-id="90121-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="90121-142">As etapas a seguir mostram como desenvolver um provedor de token personalizado que os caches tokens emitidos e integrá-lo com o WCF: segurança.</span><span class="sxs-lookup"><span data-stu-id="90121-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
#### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="90121-143">Para desenvolver um provedor de token personalizado</span><span class="sxs-lookup"><span data-stu-id="90121-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="90121-144">Escreva um provedor de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="90121-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="90121-145">O exemplo implementa um provedor de token personalizado que retorna um token de segurança recuperado de um cache.</span><span class="sxs-lookup"><span data-stu-id="90121-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="90121-146">Para executar essa tarefa, o provedor de token personalizado é derivado de <xref:System.IdentityModel.Selectors.SecurityTokenProvider> classe e substitui o <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> método.</span><span class="sxs-lookup"><span data-stu-id="90121-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="90121-147">Esse método tenta obter um token do cache, ou se um token não pode ser encontrado no cache, recupera um token do provedor subjacente e, em seguida, armazena em cache esse token.</span><span class="sxs-lookup"><span data-stu-id="90121-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="90121-148">Em ambos os casos o método retorna um `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="90121-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. <span data-ttu-id="90121-149">Escreva um Gerenciador de token de segurança personalizada.</span><span class="sxs-lookup"><span data-stu-id="90121-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="90121-150">O <xref:System.IdentityModel.Selectors.SecurityTokenManager> é usado para criar um <xref:System.IdentityModel.Selectors.SecurityTokenProvider> para um determinado <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> que é passado para ele no `CreateSecurityTokenProvider` método.</span><span class="sxs-lookup"><span data-stu-id="90121-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="90121-151">Gerenciador de token de segurança também é usado para criar os autenticadores de token e serializadores de token, mas esses não são cobertos por este exemplo.</span><span class="sxs-lookup"><span data-stu-id="90121-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="90121-152">Neste exemplo, o Gerenciador de token de segurança personalizada herda o <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> classe e substitui o `CreateSecurityTokenProvider` método para retornar o provedor de token personalizado quando os requisitos de token passados indicam que um token emitido é solicitado.</span><span class="sxs-lookup"><span data-stu-id="90121-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```  
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="90121-153">Grave uma credencial de cliente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="90121-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="90121-154">Uma classe de credenciais do cliente é usada para representar as credenciais que são configuradas para o proxy de cliente e cria a segurança Gerenciador de token é usado para obter os autenticadores de token, provedores de token e serializadores de token.</span><span class="sxs-lookup"><span data-stu-id="90121-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```  
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        Get  
        {  
          return this.cache;  
        }  
        Set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. <span data-ttu-id="90121-155">Implemente o cache de token.</span><span class="sxs-lookup"><span data-stu-id="90121-155">Implement the token cache.</span></span> <span data-ttu-id="90121-156">A implementação de exemplo usa uma classe base abstrata por meio dos quais os consumidores de um cache de token determinado interagem com o cache.</span><span class="sxs-lookup"><span data-stu-id="90121-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="90121-157">Para o cliente usar a credencial de cliente personalizado, o exemplo exclui a classe de credencial de cliente padrão e fornece a nova classe de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="90121-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="90121-158">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="90121-158">Running the sample</span></span>  
 <span data-ttu-id="90121-159">Consulte as instruções para executar o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="90121-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="90121-160">Quando você executar o exemplo, a solicitação de token de segurança é mostrada na janela do console de serviço de Token de segurança.</span><span class="sxs-lookup"><span data-stu-id="90121-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="90121-161">As respostas e solicitações de operação são exibidas nas janelas do console de cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="90121-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="90121-162">Pressione ENTER em qualquer uma das janelas do console para fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="90121-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="90121-163">O arquivo em lotes de Setup. cmd</span><span class="sxs-lookup"><span data-stu-id="90121-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="90121-164">O arquivo em lotes de Setup. cmd incluído com este exemplo permite que você configure o servidor e o serviço de token de segurança com certificados relevantes para executar um aplicativo hospedado internamente.</span><span class="sxs-lookup"><span data-stu-id="90121-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="90121-165">O arquivo em lotes cria dois certificados que no CurrentUser/TrustedPeople repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="90121-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="90121-166">O primeiro certificado tem um nome de assunto de CN = STS e é usado pelo serviço de Token de segurança para assinar os tokens de segurança que emite ao cliente.</span><span class="sxs-lookup"><span data-stu-id="90121-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="90121-167">O segundo certificado tem um nome de assunto de CN = localhost e é usado pelo serviço de Token de segurança para criptografar um segredo para que o serviço pode descriptografá-la.</span><span class="sxs-lookup"><span data-stu-id="90121-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="90121-168">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="90121-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="90121-169">Execute o arquivo Setup. cmd para criar os certificados necessários.</span><span class="sxs-lookup"><span data-stu-id="90121-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="90121-170">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="90121-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="90121-171">Certifique-se de que todos os projetos na solução são criados (compartilhado, RSTRSTR, serviço, SecurityTokenService e cliente).</span><span class="sxs-lookup"><span data-stu-id="90121-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="90121-172">Certifique-se de que Service.exe e SecurityTokenService.exe estão sendo executados com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="90121-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="90121-173">Execute Client.exe.</span><span class="sxs-lookup"><span data-stu-id="90121-173">Run Client.exe.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="90121-174">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="90121-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="90121-175">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="90121-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90121-176">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="90121-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="90121-177">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="90121-177">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="90121-178">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="90121-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="90121-179">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="90121-179">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
