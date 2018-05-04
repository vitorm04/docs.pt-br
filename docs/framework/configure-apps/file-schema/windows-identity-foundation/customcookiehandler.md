---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b974767aa86801bff234e200e1fce021bfc422c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomcookiehandlergt"></a>&lt;customCookieHandler&gt;
Define o tipo de manipulador de cookie personalizado. Esse elemento só pode estar presente se a `mode` atributo o `<cookieHandler>` elemento é "Custom". O tipo personalizado deve ser derivado de <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
 \<System >  
\<federationConfiguration >  
\<cookieHandler >  
\<customCookieHandler >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Especifica um tipo personalizado que deriva de <xref:System.IdentityModel.Services.CookieHandler> classe. Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> usa para ler e gravar cookies.|  
  
## <a name="remarks"></a>Comentários  
 Quando você especificar um manipulador personalizado de cookie, definindo o `mode` atributo do `<cookieHandler>` elemento como "Custom", você deve especificar o tipo do manipulador de cookie personalizado, incluindo um `<customCookieHandler>` elemento filho que faz referência ao tipo de manipulador de cookie. Esse elemento não pode ser especificado quando o `mode` atributo é definido como "Em partes" ou "Padrão". Manipuladores de cookie personalizado devem derivar do <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
 O `<customCookieHandler>` elemento é representado pela <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir configura o SAM para usar um manipulador personalizado de cookie do tipo `MyNamespace.MyCustomCookieHandler`.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Services.CookieHandler>
