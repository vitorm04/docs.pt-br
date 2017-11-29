---
title: '&lt;pnrpPeerResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd93bdadec120050813fcc1097d3041d6be94f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpnrppeerresolvergt"></a>&lt;pnrpPeerResolver&gt;
Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor. Esse elemento é opcional porque o PNRP é o resolvedor padrão.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<pnrpResolver >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|resolverType|Uma cadeia de caracteres que especifica o resolvedor a ser usado. Esse atributo é opcional. Se não for definido, ou se ele for definido como uma cadeia de caracteres vazia, o PNRP é usado.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="example"></a>Exemplo  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Resolvedor Peer](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
