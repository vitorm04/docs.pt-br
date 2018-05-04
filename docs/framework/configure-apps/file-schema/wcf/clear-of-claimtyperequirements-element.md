---
title: '&lt;limpar&gt; elemento &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: ca8ea91f5806a6cedc98729de1c45ab6b5de6afb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a>&lt;limpar&gt; elemento &lt;claimTypeRequirements&gt;
Especifica que todas as declarações de tipos a serem removidos na credencial federada. Isso garante que a coleção começa vazia.  
  
 \<system.ServiceModel>  
\<associações >  
\<wsFederatedBinding>  
\<associação >  
\<segurança >  
\<message>  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Especifica uma coleção de tipos de declaração necessária. Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> Em um cenário federado, serviços de estado os requisitos de credenciais de entrada. Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração. Cada elemento na coleção Especifica os tipos de declarações obrigatórias e opcionais que deve aparecer em uma credencial federada.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
