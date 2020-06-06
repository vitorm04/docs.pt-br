---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735945"
---
# \<useManagedPresentation>
<span data-ttu-id="bcd37-101">Um elemento de associação usado para comunicar-se com um serviço de token de segurança de CardSpace que dá suporte ao perfil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="bcd37-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="bcd37-102">Este elemento não tem nenhum atributo e está presente como uma opção vazia.</span><span class="sxs-lookup"><span data-stu-id="bcd37-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="bcd37-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bcd37-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcd37-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bcd37-104">Attributes and Elements</span></span>  
 <span data-ttu-id="bcd37-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bcd37-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcd37-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="bcd37-106">Attributes</span></span>  
 <span data-ttu-id="bcd37-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bcd37-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bcd37-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bcd37-108">Child Elements</span></span>  
 <span data-ttu-id="bcd37-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bcd37-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bcd37-110">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bcd37-110">Parent Elements</span></span>  
  
|<span data-ttu-id="bcd37-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="bcd37-111">Element</span></span>|<span data-ttu-id="bcd37-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcd37-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="bcd37-113">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="bcd37-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcd37-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="bcd37-114">Remarks</span></span>  
 <span data-ttu-id="bcd37-115">Esse elemento é usado por um provedor de identidade para expressar em sua política o fato de que ele dá suporte ao perfil do CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="bcd37-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="bcd37-116">Provedores de identidade que publicam tal declaração de política devem ser capazes de emitir tokens com base nesse perfil do CardSpace.</span><span class="sxs-lookup"><span data-stu-id="bcd37-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd37-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="bcd37-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bcd37-118">Associações</span><span class="sxs-lookup"><span data-stu-id="bcd37-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bcd37-119">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="bcd37-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bcd37-120">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bcd37-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
