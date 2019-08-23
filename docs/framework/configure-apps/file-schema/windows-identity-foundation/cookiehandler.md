---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 6c62100b2445ae10a83ebd9e7d154a6e2aa14e0b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942794"
---
# <a name="cookiehandler"></a>\<> cookieHandler
Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) usa para ler e gravar cookies.  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<> cookieHandler  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Especifica o nome de base para todos os cookies gravados. O padrão é "FedAuth".|  
|path|Especifica o valor do caminho para todos os cookies gravados. O padrão é "HttpRuntime. AppDomainAppVirtualPath".|  
|modo|Um dos <xref:System.IdentityModel.Services.CookieHandlerMode> valores que especifica o tipo de manipulador de cookies usado pelo Sam. Os valores a seguir podem ser usados:<br /><br /> -"Padrão" — o mesmo que "em partes".<br />-"Em partes" — usa uma instância da <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Esse manipulador de cookies garante que os cookies individuais não excedam um tamanho máximo definido. Ele realiza isso por meio de "Agrupamento" de um cookie lógico em vários cookies durante a transmissão.<br />-"Custom" — usa uma instância de uma classe personalizada derivada de <xref:System.IdentityModel.Services.CookieHandler>. A classe derivada é referenciada pelo `<customCookieHandler>` elemento filho.<br /><br /> O padrão é "default".|  
|persistentSessionLifetime|Especifica o tempo de vida de sessões persistentes. Se for zero, sessões transitórias serão sempre usadas. O valor padrão é "0:0:0", que especifica uma sessão transitória. O valor máximo é "365:0:0", que especifica uma sessão de 365 dias. O valor deve ser especificado de acordo com a seguinte restrição `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`:, em que o valor mais à esquerda especifica dias, o valor do meio (se presente) especifica horas e o valor mais à direita (se presente) especifica minutos.|  
|requireSsl|Especifica se o sinalizador "seguro" é emitido para todos os cookies gravados. Se esse valor for definido, os cookies da sessão de entrada só estarão disponíveis por HTTPS. O padrão é "true".|  
|hideFromScript|Controla se o sinalizador "HttpOnly" é emitido para todos os cookies gravados. Determinados navegadores da Web honram esse sinalizador mantendo o script do lado do cliente de acessar o valor do cookie. O padrão é "true".|  
|domínio|O valor de domínio para todos os cookies gravados. O padrão é "".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Esse elemento só poderá estar presente se o `mode` atributo `<cookieHandler>` do elemento for "padrão" ou "em bloco".|  
|[\<customCookieHandler>](customcookiehandler.md)|Define o tipo de manipulador de cookies personalizado. Esse elemento deve estar presente se o `mode` atributo `<cookieHandler>` do elemento for "Custom". Ele não pode estar presente para nenhum outro valor do `mode` atributo. O tipo personalizado deve ser derivado da <xref:System.IdentityModel.Services.CookieHandler> classe.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Contém as configurações que definem <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> o (WSFAM) e <xref:System.IdentityModel.Services.SessionAuthenticationModule> o (Sam).|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.IdentityModel.Services.CookieHandler> é responsável por ler e gravar cookies brutos no nível do protocolo http. Você pode configurar um <xref:System.IdentityModel.Services.ChunkedCookieHandler> ou um manipulador <xref:System.IdentityModel.Services.CookieHandler> de cookie personalizado derivado da classe.  
  
 Para configurar um manipulador de cookie em bloco, defina o atributo Mode como "em bloco" ou "padrão". O tamanho de parte padrão é 2000 bytes, mas você pode opcionalmente especificar um tamanho de parte diferente, `<chunkedCookieHandler>` incluindo um elemento filho.  
  
 Para configurar um manipulador de cookie personalizado, defina o atributo Mode como "Custom". Você também deve especificar um `<customCookieHandler>` elemento filho que referencie o tipo de seu manipulador personalizado.  
  
 O `<cookieHandler>` elemento é representado <xref:System.IdentityModel.Services.CookieHandlerElement> pela classe. O manipulador <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> de cookies que foi especificado na configuração está disponível na Propriedade do conjunto de objetosnapropriedade.<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra `<cookieHandler>` um elemento. Neste exemplo, como o `mode` atributo não é especificado, o manipulador de cookies padrão será usado pelo Sam. Essa é uma instância da <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Como o `<chunkedCookieHandler>` elemento filho não é especificado, o tamanho de bloco padrão será usado. O HTTPS não será necessário porque o `requireSsl` atributo está definido `false`.  
  
> [!WARNING]
>  Neste exemplo, o HTTPS não é necessário para gravar cookies de sessão. Isso ocorre porque o `requireSsl` atributo `<cookieHandler>` no elemento está definido como `false`. Essa configuração não é recomendada para a maioria dos ambientes de produção, pois pode representar um risco de segurança.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
