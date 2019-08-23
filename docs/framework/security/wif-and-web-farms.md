---
title: WIF e Web Farms
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: e6806971bd2260785d66bfdb54a3e2938043c746
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967184"
---
# <a name="wif-and-web-farms"></a><span data-ttu-id="3c4d8-102">WIF e Web Farms</span><span class="sxs-lookup"><span data-stu-id="3c4d8-102">WIF and Web Farms</span></span>
<span data-ttu-id="3c4d8-103">Ao usar o WIF (Windows Identity Foundation) para proteger os recursos de um aplicativo RP (terceira parte confiável) implantado em uma web farm, siga etapas específicas para garantir que o WIF possa processar tokens de instâncias do aplicativo RP em execução em diferentes computadores no farm.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-103">When you use Windows Identity Foundation (WIF) to secure the resources of a relying party (RP) application that is deployed in a web farm, you must take specific steps to ensure that WIF can process tokens from instances of the RP application running on different computers in the farm.</span></span> <span data-ttu-id="3c4d8-104">Esse processamento inclui validação de assinaturas de token de sessão, criptografia e descriptografia de tokens de sessão, cache de tokens de sessão e detecção de tokens de segurança reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-104">This processing includes validating session token signatures, encrypting and decrypting session tokens, caching session tokens, and detecting replayed security tokens.</span></span>  
  
 <span data-ttu-id="3c4d8-105">No caso típico, quando o WIF é usado para proteger recursos de um aplicativo RP – independentemente de o RP estar em execução em um único computador ou em uma web farm –, uma sessão é estabelecida com o cliente com base no token de segurança obtido do STS (serviço de token de segurança).</span><span class="sxs-lookup"><span data-stu-id="3c4d8-105">In the typical case, when WIF is used to secure resources of an RP application – whether the RP is running on a single computer or in a web farm -- a session is established with the client based on the security token that was obtained from the security token service (STS).</span></span> <span data-ttu-id="3c4d8-106">Isso ocorre para evitar forçar o cliente a se autenticar no STS para cada recurso do aplicativo que é protegido usando o WIF.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-106">This is to avoid forcing the client to have to authenticate at the STS for every application resource that is secured using WIF.</span></span> <span data-ttu-id="3c4d8-107">Para obter mais informações sobre como o WIF manipula as sessões, consulte [Gerenciamento de sessões do WIF](../../../docs/framework/security/wif-session-management.md).</span><span class="sxs-lookup"><span data-stu-id="3c4d8-107">For more information about how WIF handles sessions, see [WIF Session Management](../../../docs/framework/security/wif-session-management.md).</span></span>  
  
 <span data-ttu-id="3c4d8-108">Quando as configurações padrão são usadas, o WIF faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3c4d8-108">When default settings are used, WIF does the following:</span></span>  
  
- <span data-ttu-id="3c4d8-109">Ele usa uma instância da classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> para ler e gravar um token de sessão (uma instância da classe <xref:System.IdentityModel.Tokens.SessionSecurityToken>) que leva as declarações e outras informações sobre o token de segurança que foi usado para autenticação, bem como informações sobre a própria sessão.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-109">It uses an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class to read and write a session token (an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityToken> class) that carries the claims and other information about the security token that was used for authentication as well as information about the session itself.</span></span> <span data-ttu-id="3c4d8-110">O token de sessão é empacotado e armazenado em um cookie de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-110">The session token is packaged and stored in a session cookie.</span></span> <span data-ttu-id="3c4d8-111">Por padrão, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> usa a classe <xref:System.IdentityModel.ProtectedDataCookieTransform>, que usa a DPAPI (API de Proteção de Dados), para proteger o token de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-111">By default, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> uses the <xref:System.IdentityModel.ProtectedDataCookieTransform> class, which uses the Data Protection API (DPAPI), to protect the session token.</span></span> <span data-ttu-id="3c4d8-112">A DPAPI fornece proteção usando as credenciais do usuário ou do computador e armazena os dados de chave no perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-112">The DPAPI provides protection by using the user or machine credentials and stores the key data in the user profile.</span></span>  
  
- <span data-ttu-id="3c4d8-113">Ela usa uma implementação padrão na memória da classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> para armazenar e processar o token de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-113">It uses a default, in-memory implementation of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class to store and process the session token.</span></span>  
  
 <span data-ttu-id="3c4d8-114">Essas configurações padrão funcionam em cenários em que o aplicativo RP é implantado em um único computador. No entanto, quando implantado em uma web farm, cada solicitação HTTP pode ser enviada e processada por outra instância do aplicativo RP em execução em um computador diferente.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-114">These default settings work in scenarios in which the RP application is deployed on a single computer; however, when deployed in a web farm, each HTTP request may be sent to and processed by a different instance of the RP application running on a different computer.</span></span> <span data-ttu-id="3c4d8-115">Nesse cenário, as configurações padrão do WIF descritas acima não funcionarão porque a proteção de token e o cache de token dependem de um computador específico.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-115">In this scenario, the default WIF settings described above will not work because both token protection and token caching are dependent on a specific computer.</span></span>  
  
 <span data-ttu-id="3c4d8-116">Para implantar um aplicativo RP em uma web farm, você deve garantir que o processamento de tokens de sessão (bem como dos tokens reproduzidos) não depende de o aplicativo ser executado em um computador específico.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-116">To deploy an RP application in a web farm, you must ensure that the processing of session tokens (as well as of replayed tokens) is not dependent on the application running on a specific computer.</span></span> <span data-ttu-id="3c4d8-117">Uma forma de fazer isso é implementar o aplicativo RP de modo que ele use a funcionalidade fornecida pelo elemento de configuração `<machineKey>` do ASP.NET e forneça o cache distribuído para processar tokens de sessão e tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-117">One way to do this is to implement your RP application so that it uses the functionality provided by the ASP.NET `<machineKey>` configuration element and provides distributed caching for processing session tokens and replayed tokens.</span></span> <span data-ttu-id="3c4d8-118">O elemento `<machineKey>` permite especificar as chaves necessárias para validar, criptografar e descriptografar tokens em um arquivo de configuração, que possibilita especificar as mesmas chaves em computadores diferentes na web farm.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-118">The `<machineKey>` element allows you to specify the keys needed to validate, encrypt, and decrypt tokens in a configuration file, which enables you to specify the same keys on different computers in the web farm.</span></span> <span data-ttu-id="3c4d8-119">O WIF fornece um manipulador de token de sessão especializado, o <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, que protege os tokens usando as chaves especificadas no elemento `<machineKey>`.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-119">WIF provides a specialized session token handler, the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, that protects tokens by using the keys specified in the `<machineKey>` element.</span></span> <span data-ttu-id="3c4d8-120">Para implementar essa estratégia, siga estas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="3c4d8-120">To implement this strategy, you can follow these guidelines:</span></span>  
  
- <span data-ttu-id="3c4d8-121">Use o elemento `<machineKey>` do ASP.NET na configuração para especificar explicitamente as chaves de criptografia e autenticação que podem ser usadas nos computadores do farm.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-121">Use the ASP.NET `<machineKey>` element in configuration to explicitly specify signing and encryption keys that can be used across computers in the farm.</span></span> <span data-ttu-id="3c4d8-122">O XML a seguir mostra a especificação do elemento `<machineKey>` no elemento `<system.web>` em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-122">The following XML shows the specification of the `<machineKey>` element under the `<system.web>` element in a configuration file.</span></span>  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- <span data-ttu-id="3c4d8-123">Configure o aplicativo para usar o <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> adicionando-o à coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-123">Configure the application to use the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> by adding it to the token handler collection.</span></span> <span data-ttu-id="3c4d8-124">Primeiro você deverá remover o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (ou qualquer manipulador derivado da classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>) da coleção de manipuladores de token se um manipulador desse tipo estiver presente.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-124">You must first remove the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (or any handler derived from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class) from the token handler collection if such a handler is present.</span></span> <span data-ttu-id="3c4d8-125">O <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> usa a classe <xref:System.IdentityModel.Services.MachineKeyTransform>, que protege os dados de cookie da sessão usando o material criptográfico especificado no elemento `<machineKey>`.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-125">The <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> uses the <xref:System.IdentityModel.Services.MachineKeyTransform> class, which protects the session cookie data by using the cryptographic material specified in the `<machineKey>` element.</span></span> <span data-ttu-id="3c4d8-126">O XML a seguir mostra como adicionar o <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> a uma coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-126">The following XML shows how to add the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> to a token handler collection.</span></span>  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- <span data-ttu-id="3c4d8-127">Derive de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> e implemente o cache distribuído ou seja, um cache que é acessível em todos os computadores do farm no qual o RP pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-127">Derive from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and implement distributed caching, that is, a cache that is accessible from all computers in the farm on which the RP might run.</span></span> <span data-ttu-id="3c4d8-128">Configure o RP para usar o cache distribuído especificando o elemento [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-128">Configure the RP to use your distributed cache by specifying the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element in the configuration file.</span></span> <span data-ttu-id="3c4d8-129">Substitua o método <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> na classe derivada para implementar os elementos filho do elemento `<sessionSecurityTokenCache>`, caso eles sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-129">You can override the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> method in your derived class to implement child elements of the `<sessionSecurityTokenCache>` element if they are required.</span></span>  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     <span data-ttu-id="3c4d8-130">Uma maneira de implementar o cache distribuído é fornecer um front-end do WCF ao cache personalizado.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-130">One way to implement distributed caching is to provide a WCF front end for your custom cache.</span></span> <span data-ttu-id="3c4d8-131">Para obter mais informações sobre como implementar um serviço de cache do WCF, consulte [O serviço de cache do WCF](#BKMK_TheWCFCachingService).</span><span class="sxs-lookup"><span data-stu-id="3c4d8-131">For more information about implementing a WCF caching service, see [The WCF Caching Service](#BKMK_TheWCFCachingService).</span></span> <span data-ttu-id="3c4d8-132">Para obter mais informações sobre como implementar um cliente do WCF que pode ser usado pelo aplicativo RP para chamar o serviço de cache, consulte [O cliente de cache do WCF](#BKMK_TheWCFClient).</span><span class="sxs-lookup"><span data-stu-id="3c4d8-132">For more information about implementing a WCF client that the RP application can use to call the caching service, see [The WCF Caching Client](#BKMK_TheWCFClient).</span></span>  
  
- <span data-ttu-id="3c4d8-133">Se o aplicativo detectar tokens reproduzidos, siga uma estratégia de cache distribuído semelhante para o cache de reprodução de token derivando de <xref:System.IdentityModel.Tokens.TokenReplayCache> e apontando para o cache de reprodução de token no serviço de cache do elemento de configuração [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md).</span><span class="sxs-lookup"><span data-stu-id="3c4d8-133">If your application detects replayed tokens you must follow a similar distributed caching strategy for the token replay cache by deriving from <xref:System.IdentityModel.Tokens.TokenReplayCache> and pointing to your token replay caching service in the [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) configuration element.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3c4d8-134">Todo o exemplo de XML e código neste tópico é tirado do exemplo de [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) .</span><span class="sxs-lookup"><span data-stu-id="3c4d8-134">All of the example XML and code in this topic is taken from the [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3c4d8-135">Os exemplos deste tópico são fornecidos no estado em que se encontram e não se destinam a serem usados no código de produção sem modificação.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-135">The examples in this topic are provided as-is and are not intended to be used in production code without modification.</span></span>  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a><span data-ttu-id="3c4d8-136">O serviço de cache do WCF</span><span class="sxs-lookup"><span data-stu-id="3c4d8-136">The WCF Caching Service</span></span>  
 <span data-ttu-id="3c4d8-137">A interface a seguir define o contrato entre o serviço de cache do WCF e o cliente do WCF usado pelo aplicativo de terceira parte confiável para se comunicar com ele.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-137">The following interface defines the contract between the WCF caching service and the WCF client used by the relying party application to communicate with it.</span></span> <span data-ttu-id="3c4d8-138">Basicamente, ela expõe os métodos da classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> como operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-138">It essentially exposes the methods of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class as service operations.</span></span>  
  
```  
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 <span data-ttu-id="3c4d8-139">O código a seguir mostra a implementação do serviço de cache do WCF.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-139">The following code shows the implementation of the WCF caching service.</span></span> <span data-ttu-id="3c4d8-140">Neste exemplo, o padrão, o cache de token de sessão na memória implementado pelo WIF, é usado.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-140">In this example, the default, in-memory session token cache implemented by WIF is used.</span></span> <span data-ttu-id="3c4d8-141">Como alternativa, você pode implementar um cache durável com suporte de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-141">Alternatively, you could implement a durable cache backed by a database.</span></span> <span data-ttu-id="3c4d8-142">`ISessionSecurityTokenCacheService` define a interface mostrada acima.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-142">`ISessionSecurityTokenCacheService` defines the interface shown above.</span></span> <span data-ttu-id="3c4d8-143">Neste exemplo, nem todos os métodos necessários para implementar a interface são mostrados, para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-143">In this example, not all of the methods required to implement the interface are shown for brevity.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a><span data-ttu-id="3c4d8-144">O cliente de cache do WCF</span><span class="sxs-lookup"><span data-stu-id="3c4d8-144">The WCF Caching Client</span></span>  
 <span data-ttu-id="3c4d8-145">Esta seção mostra a implementação de uma classe que é derivada de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> e as chamadas dos representantes ao serviço de cache.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-145">This section shows the implementation of a class that derives from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and that delegates calls to the caching service.</span></span> <span data-ttu-id="3c4d8-146">Configure o aplicativo RP para usar essa classe por meio do elemento [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) como o XML a seguir</span><span class="sxs-lookup"><span data-stu-id="3c4d8-146">You configure the RP application to use this class through the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element as in the following XML</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 <span data-ttu-id="3c4d8-147">A classe substitui o método <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> para obter o ponto de extremidade de serviço do elemento filho `<cacheServiceAddress>` personalizado do elemento `<sessionSecurityTokenCache>`.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-147">The class overrides the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> method to get the service endpoint from the custom `<cacheServiceAddress>` child element of the `<sessionSecurityTokenCache>` element.</span></span> <span data-ttu-id="3c4d8-148">Ela usa esse ponto de extremidade para inicializar um canal `ISessionSecurityTokenCacheService` por meio do qual ele pode se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-148">It uses this endpoint to initialize an `ISessionSecurityTokenCacheService` channel over which it can communicate with the service.</span></span>  <span data-ttu-id="3c4d8-149">Neste exemplo, nem todos os métodos necessários para implementar a classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> são mostrados, para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="3c4d8-149">In this example, not all of the methods required to implement the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class are shown for brevity.</span></span>  
  
```  
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c4d8-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c4d8-150">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [<span data-ttu-id="3c4d8-151">Gerenciamento de sessões WIF</span><span class="sxs-lookup"><span data-stu-id="3c4d8-151">WIF Session Management</span></span>](../../../docs/framework/security/wif-session-management.md)
