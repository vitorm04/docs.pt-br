---
title: '&lt;cookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 88e968d025c959ec33674a9d8edb5e63341433ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) usa para ler e gravar cookies.  
  
 \<System >  
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
|name|Especifica o nome de base para qualquer cookie gravado. O padrão é "FedAuth".|  
|path|Especifica o valor do caminho para qualquer cookie gravado. O padrão é "Appdomainappvirtualpath".|  
|modo|Uma da <xref:System.IdentityModel.Services.CookieHandlerMode> valores que especifica o tipo de manipulador de cookie usado pelo SAM. Os valores a seguir podem ser usados:<br /><br /> -"Padrão" — o mesmo que "Em partes".<br />-"Blocos" – usa uma instância do <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Este manipulador de cookie garante que os cookies individuais não exceder um tamanho máximo do conjunto. Isso é feito através de "agrupamento" potencialmente um cookie lógico em um número de cookies no-durante a transmissão.<br />-"Custom" – usa uma instância de uma classe personalizada derivada de <xref:System.IdentityModel.Services.CookieHandler>. A classe derivada é referenciada pelo `<customCookieHandler>` elemento filho.<br /><br /> O padrão é "Padrão".|  
|persistentSessionLifetime|Especifica o tempo de vida de sessões persistentes. Se for zero, sessões transitórias são sempre usadas. O valor padrão é "0:0:0", que especifica uma sessão temporária. O valor máximo é "365:0:0", que especifica uma sessão de 365 dias. O valor deve ser especificado de acordo com a seguinte restrição: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, onde o valor mais à esquerda especifica os dias, o valor intermediário (se houver) especifica horas e minutos de Especifica o valor mais à direita (se houver).|  
|RequireSsl|Especifica se o sinalizador "Secure" é emitido para qualquer cookie gravado. Se esse valor for definido, os cookies de sessão de entrada só estará disponíveis via HTTPS. O padrão é "true".|  
|hideFromScript|Controla se o sinalizador "HttpOnly" é emitido para qualquer cookie gravado. Alguns navegadores da web aceitam esse sinalizador, mantendo o script do lado do cliente acessem o valor do cookie. O padrão é "true".|  
|domínio|O valor de domínio para qualquer cookie gravado. O padrão é "".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Configura o <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Esse elemento só pode estar presente se a `mode` atributo do `<cookieHandler>` elemento é "Padrão" ou "Blocos".|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Define o tipo de manipulador de cookie personalizado. Esse elemento deve estar presente se a `mode` atributo o `<cookieHandler>` elemento é "Custom". Ele não pode estar presente para todos os outros valores da `mode` atributo. O tipo personalizado deve ser derivado de <xref:System.IdentityModel.Services.CookieHandler> classe.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contém as configurações que definir o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.IdentityModel.Services.CookieHandler> é responsável por nível de protocolo de leitura e gravação de cookies brutos no HTTP. Você pode configurar o um <xref:System.IdentityModel.Services.ChunkedCookieHandler> ou um manipulador de cookie personalizado derivado de <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
 Para configurar um manipulador de cookie em partes, defina o atributo mode "Em partes" ou "Padrão". O tamanho da parte padrão é 2000 bytes, mas é necessário especificar um tamanho de bloco diferentes, incluindo um `<chunkedCookieHandler>` elemento filho.  
  
 Para configurar um manipulador de cookie personalizado, defina o atributo mode para "Custom". Você também deve especificar um `<customCookieHandler>` elemento filho que referencia o tipo do seu manipulador personalizado.  
  
 O `<cookieHandler>` elemento é representado pela <xref:System.IdentityModel.Services.CookieHandlerElement> classe. O manipulador de cookie que foi especificado na configuração está disponível na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> propriedade o <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objeto definido no <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra um `<cookieHandler>` elemento. Neste exemplo, porque o `mode` atributo não for especificado, o manipulador de cookie padrão será usado pelo SAM. Essa é uma instância do <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Porque o `<chunkedCookieHandler>` elemento filho não for especificado, o tamanho da parte padrão será usado. HTTPS não será mais necessário porque o `requireSsl` atributo é definido `false`.  
  
> [!WARNING]
>  Neste exemplo, HTTPS não é necessário para gravar os cookies de sessão. Isso ocorre porque o `requireSsl` atributo no `<cookieHandler>` é definido como `false`. Essa configuração não é recomendável para a maioria dos ambientes de produção, pois ele pode representar um risco de segurança.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
