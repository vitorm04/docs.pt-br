---
title: '&lt;limpar&gt; elemento &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: c64e5450e01fdb011eb726f3bef1a85a5698d0d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568329"
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a>&lt;limpar&gt; elemento &lt;claimTypeRequirements&gt;
Especifica que todos os tipos de declaração a serem removidos na credencial federada. Isso garante que a coleção começa vazia.  
  
 \<system.ServiceModel>  
\<bindings>  
\<wsFederatedBinding>  
\<binding>  
\<segurança >  
\<message>  
\<claimTypeRequirements>  
  
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
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Especifica uma coleção de tipos de declaração exigidos. Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada. Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração. Cada elemento nesta coleção Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer em uma credencial federada.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
