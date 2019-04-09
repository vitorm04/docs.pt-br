---
title: WIF e Web Farms
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 2f95213390187648c9f58b9b2bf2d5e3f49fb860
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135350"
---
# <a name="wif-and-web-farms"></a>WIF e Web Farms
Ao usar o WIF (Windows Identity Foundation) para proteger os recursos de um aplicativo RP (terceira parte confiável) implantado em uma web farm, siga etapas específicas para garantir que o WIF possa processar tokens de instâncias do aplicativo RP em execução em diferentes computadores no farm. Esse processamento inclui validação de assinaturas de token de sessão, criptografia e descriptografia de tokens de sessão, cache de tokens de sessão e detecção de tokens de segurança reproduzidos.  
  
 No caso típico, quando o WIF é usado para proteger recursos de um aplicativo RP – independentemente de o RP estar em execução em um único computador ou em uma web farm –, uma sessão é estabelecida com o cliente com base no token de segurança obtido do STS (serviço de token de segurança). Isso ocorre para evitar forçar o cliente a se autenticar no STS para cada recurso do aplicativo que é protegido usando o WIF. Para obter mais informações sobre como o WIF manipula as sessões, consulte [Gerenciamento de sessões do WIF](../../../docs/framework/security/wif-session-management.md).  
  
 Quando as configurações padrão são usadas, o WIF faz o seguinte:  
  
-   Ele usa uma instância da classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> para ler e gravar um token de sessão (uma instância da classe <xref:System.IdentityModel.Tokens.SessionSecurityToken>) que leva as declarações e outras informações sobre o token de segurança que foi usado para autenticação, bem como informações sobre a própria sessão. O token de sessão é empacotado e armazenado em um cookie de sessão. Por padrão, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> usa a classe <xref:System.IdentityModel.ProtectedDataCookieTransform>, que usa a DPAPI (API de Proteção de Dados), para proteger o token de sessão. A DPAPI fornece proteção usando as credenciais do usuário ou do computador e armazena os dados de chave no perfil do usuário.  
  
-   Ela usa uma implementação padrão na memória da classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> para armazenar e processar o token de sessão.  
  
 Essas configurações padrão funcionam em cenários em que o aplicativo RP é implantado em um único computador. No entanto, quando implantado em uma web farm, cada solicitação HTTP pode ser enviada e processada por outra instância do aplicativo RP em execução em um computador diferente. Nesse cenário, as configurações padrão do WIF descritas acima não funcionarão porque a proteção de token e o cache de token dependem de um computador específico.  
  
 Para implantar um aplicativo RP em uma web farm, você deve garantir que o processamento de tokens de sessão (bem como dos tokens reproduzidos) não depende de o aplicativo ser executado em um computador específico. Uma forma de fazer isso é implementar o aplicativo RP de modo que ele use a funcionalidade fornecida pelo elemento de configuração `<machineKey>` do ASP.NET e forneça o cache distribuído para processar tokens de sessão e tokens reproduzidos. O elemento `<machineKey>` permite especificar as chaves necessárias para validar, criptografar e descriptografar tokens em um arquivo de configuração, que possibilita especificar as mesmas chaves em computadores diferentes na web farm. O WIF fornece um manipulador de token de sessão especializado, o <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, que protege os tokens usando as chaves especificadas no elemento `<machineKey>`. Para implementar essa estratégia, siga estas diretrizes:  
  
-   Use o elemento `<machineKey>` do ASP.NET na configuração para especificar explicitamente as chaves de criptografia e autenticação que podem ser usadas nos computadores do farm. O XML a seguir mostra a especificação do elemento `<machineKey>` no elemento `<system.web>` em um arquivo de configuração.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   Configure o aplicativo para usar o <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> adicionando-o à coleção de manipuladores de token. Primeiro você deverá remover o <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (ou qualquer manipulador derivado da classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>) da coleção de manipuladores de token se um manipulador desse tipo estiver presente. O <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> usa a classe <xref:System.IdentityModel.Services.MachineKeyTransform>, que protege os dados de cookie da sessão usando o material criptográfico especificado no elemento `<machineKey>`. O XML a seguir mostra como adicionar o <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> a uma coleção de manipuladores de token.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   Derive de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> e implemente o cache distribuído ou seja, um cache que é acessível em todos os computadores do farm no qual o RP pode ser executado. Configure o RP para usar o cache distribuído especificando o elemento [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) no arquivo de configuração. Substitua o método <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> na classe derivada para implementar os elementos filho do elemento `<sessionSecurityTokenCache>`, caso eles sejam necessários.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Uma maneira de implementar o cache distribuído é fornecer um front-end do WCF ao cache personalizado. Para obter mais informações sobre como implementar um serviço de cache do WCF, consulte [O serviço de cache do WCF](#BKMK_TheWCFCachingService). Para obter mais informações sobre como implementar um cliente do WCF que pode ser usado pelo aplicativo RP para chamar o serviço de cache, consulte [O cliente de cache do WCF](#BKMK_TheWCFClient).  
  
-   Se o aplicativo detectar tokens reproduzidos, siga uma estratégia de cache distribuído semelhante para o cache de reprodução de token derivando de <xref:System.IdentityModel.Tokens.TokenReplayCache> e apontando para o cache de reprodução de token no serviço de cache do elemento de configuração [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md).  
  
> [!IMPORTANT]
>  Todos os exemplo de XML e o código deste tópico é obtida a [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) exemplo.  
  
> [!IMPORTANT]
>  Os exemplos deste tópico são fornecidos no estado em que se encontram e não se destinam a serem usados no código de produção sem modificação.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>O serviço de cache do WCF  
 A interface a seguir define o contrato entre o serviço de cache do WCF e o cliente do WCF usado pelo aplicativo de terceira parte confiável para se comunicar com ele. Basicamente, ela expõe os métodos da classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> como operações de serviço.  
  
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
  
 O código a seguir mostra a implementação do serviço de cache do WCF. Neste exemplo, o padrão, o cache de token de sessão na memória implementado pelo WIF, é usado. Como alternativa, você pode implementar um cache durável com suporte de um banco de dados. `ISessionSecurityTokenCacheService` Define a interface mostrada acima. Neste exemplo, nem todos os métodos necessários para implementar a interface são mostrados, para fins de brevidade.  
  
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
## <a name="the-wcf-caching-client"></a>O cliente de cache do WCF  
 Esta seção mostra a implementação de uma classe que é derivada de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> e as chamadas dos representantes ao serviço de cache. Configure o aplicativo RP para usar essa classe por meio do elemento [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) como o XML a seguir  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 A classe substitui o método <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> para obter o ponto de extremidade de serviço do elemento filho `<cacheServiceAddress>` personalizado do elemento `<sessionSecurityTokenCache>`. Ela usa esse ponto de extremidade para inicializar um canal `ISessionSecurityTokenCacheService` por meio do qual ele pode se comunicar com o serviço.  Neste exemplo, nem todos os métodos necessários para implementar a classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> são mostrados, para fins de brevidade.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [Gerenciamento de sessões do WIF](../../../docs/framework/security/wif-session-management.md)
