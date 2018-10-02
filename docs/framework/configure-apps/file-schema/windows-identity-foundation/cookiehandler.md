---
title: '&lt;cookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 99bf6edb4e4f631eba292990c65c1f0c8553d8c0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046442"
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
Configura a <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) usa para ler e gravar cookies.  
  
 \<IdentityModel >  
\<federationConfiguration >  
\<cookieHandler >  
  
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
|name|Especifica o nome base dos cookies gravados. O padrão é "FedAuth".|  
|path|Especifica o valor do caminho dos cookies gravados. O padrão é "Appdomainappvirtualpath".|  
|modo|Um do <xref:System.IdentityModel.Services.CookieHandlerMode> valores que especifica o tipo de manipulador de cookie usado pelo SAM. Os valores a seguir podem ser usados:<br /><br /> -"Default" — o mesmo que "Em bloco".<br />-"Em bloco" — usa uma instância da <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Esse manipulador de cookie garante que os cookies individuais não excedam um tamanho máximo do conjunto. Isso é feito por "agrupamento" potencialmente um cookie lógico em um número de cookies no-the-wire.<br />-"Custom" – usa uma instância de uma classe personalizada derivada de <xref:System.IdentityModel.Services.CookieHandler>. A classe derivada é referenciada pelo `<customCookieHandler>` elemento filho.<br /><br /> O padrão é "Default".|  
|persistentSessionLifetime|Especifica o tempo de vida das sessões persistentes. Se for zero, sessões transitórias serão sempre usadas. O valor padrão é "0:0:0", que especifica uma sessão transitória. O valor máximo é "365:0:0", que especifica uma sessão de 365 dias. O valor deve ser especificado de acordo com a seguinte restrição: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, onde o valor mais à esquerda especifica os dias, o valor intermediário (se houver) especifica horas e minutos de Especifica o valor mais à direita (se presente).|  
|RequireSsl|Especifica se o sinalizador "Secure" é emitido para qualquer cookie gravado. Se esse valor for definido, os cookies de sessão de entrada só estará disponíveis em HTTPS. O padrão é "true".|  
|hideFromScript|Controla se o sinalizador "HttpOnly" é emitido para qualquer cookie gravado. Alguns navegadores da web honrar esse sinalizador, mantendo o script do lado do cliente de acessar o valor do cookie. O padrão é "true".|  
|domínio|O valor de domínio para qualquer cookie gravado. O padrão é "".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Esse elemento pode estar presente apenas se o `mode` atributo do `<cookieHandler>` elemento é "Default" ou "Em bloco".|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Define o tipo de manipulador de cookie personalizado. Esse elemento deve estar presente se o `mode` atributo do `<cookieHandler>` elemento é "Custom". Ele não pode estar presente para todos os outros valores da `mode` atributo. O tipo personalizado deve ser derivado de <xref:System.IdentityModel.Services.CookieHandler> classe.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contém as configurações que configuram os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.IdentityModel.Services.CookieHandler> é responsável por nível de protocolo de leitura e gravação de cookies brutos em HTTP. Você pode configurar qualquer um uma <xref:System.IdentityModel.Services.ChunkedCookieHandler> ou um manipulador de cookie personalizado derivado de <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
 Para configurar um manipulador de cookie em partes, defina o atributo mode "Em bloco" ou "Padrão". O tamanho da parte padrão é 2.000 bytes, mas, opcionalmente, você pode especificar um tamanho de bloco diferentes, incluindo um `<chunkedCookieHandler>` elemento filho.  
  
 Para configurar um manipulador de cookie personalizado, defina o atributo mode como "Custom". Você também deve especificar um `<customCookieHandler>` elemento filho que faz referência ao tipo do seu manipulador personalizado.  
  
 O `<cookieHandler>` elemento é representado pelo <xref:System.IdentityModel.Services.CookieHandlerElement> classe. O manipulador de cookie que foi especificado na configuração está disponível na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> propriedade do <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objeto definido no <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra um `<cookieHandler>` elemento. Neste exemplo, porque o `mode` atributo não for especificado, o manipulador de cookie padrão será usado pelo SAM. Essa é uma instância do <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Porque o `<chunkedCookieHandler>` elemento filho não for especificado, o tamanho do bloco padrão será usado. HTTPS não será necessária porque o `requireSsl` atributo é definido `false`.  
  
> [!WARNING]
>  Neste exemplo, HTTPS não é necessário para gravar cookies de sessão. Isso ocorre porque o `requireSsl` atributo o `<cookieHandler>` é definido como `false`. Essa configuração não é recomendada para a maioria dos ambientes de produção, como ele pode representar um risco de segurança.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
