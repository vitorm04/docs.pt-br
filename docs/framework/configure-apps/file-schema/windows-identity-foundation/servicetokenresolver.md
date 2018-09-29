---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: d4b64e2c88e153834b7cf5a83bd6258b6dfd471f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454283"
---
# <a name="ltservicetokenresolvergt"></a>&lt;serviceTokenResolver&gt;
Registra o resolvedor de token de serviço que é usado por manipuladores na coleção de manipulador de token. O resolvedor de token de serviço é usado para resolver o token de criptografia em tokens de entrada e de mensagens.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Especifica o tipo de resolvedor de token de serviço. Ambos os <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tipo ou um tipo que deriva a <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe. Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado]. Necessário.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fornece manipuladores de token de configuração para uma coleção de segurança.|  
  
## <a name="remarks"></a>Comentários  
 O resolvedor de token do serviço pode ser usado para resolver o token de criptografia em tokens de entrada e de mensagens. Ele é usado para recuperar a chave que deve ser usada para descriptografar tokens recebidos. Você deve especificar o `type` atributo. O tipo especificado pode ser <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.  
  
 Alguns manipuladores de token permitem que você especifique configurações de resolvedor de token do serviço na configuração. As configurações em manipuladores de token individuais substituem aqueles especificados na coleção de manipulador de token de segurança.  
  
> [!NOTE]
>  Especificando o `<serviceTokenResolver>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi preterido, mas ainda há suporte para compatibilidade com versões anteriores. Configurações de `<securityTokenHandlerConfiguration>` elemento substituem as o `<identityConfiguration>` elemento.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
