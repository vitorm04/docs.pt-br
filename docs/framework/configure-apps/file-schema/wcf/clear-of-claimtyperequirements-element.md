---
title: '&lt;limpar&gt; elemento &lt;claimTypeRequirements&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 69752480a7f399a202d497e12a783ffa091dd4b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a>&lt;limpar&gt; elemento &lt;claimTypeRequirements&gt;
Especifica que todas as declarações de tipos a serem removidos na credencial federada. Isso garante que a coleção começa vazia.  
  
 \<sistema. ServiceModel >  
\<associações >  
\<wsFederatedBinding >  
\<associação >  
\<segurança >  
\<mensagem >  
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
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Especifica uma coleção de tipos de declaração necessária. Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> Em um cenário federado, serviços de estado os requisitos de credenciais de entrada. Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração. Cada elemento na coleção Especifica os tipos de declarações obrigatórias e opcionais que deve aparecer em uma credencial federada.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
