---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940621"
---
# <a name="usemanagedpresentation"></a>\<useManagedPresentation>
Um elemento de associação usado para comunicar-se com um serviço de token de segurança de CardSpace que dá suporte ao perfil CardSpace de WS-Trust. Este elemento não tem nenhum atributo e está presente como uma opção vazia.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<> de associação  
\<useManagedPresentation>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento é usado por um provedor de identidade para expressar em sua política o fato de que ele dá suporte ao perfil do CardSpace de WS-Trust. Provedores de identidade que publicam tal declaração de política devem ser capazes de emitir tokens com base nesse perfil do CardSpace.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
