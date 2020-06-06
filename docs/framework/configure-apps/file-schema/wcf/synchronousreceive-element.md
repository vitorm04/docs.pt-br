---
title: Elemento <synchronousReceive>
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399504"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="dee1e-102">Elemento \<synchronousReceive></span><span class="sxs-lookup"><span data-stu-id="dee1e-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="dee1e-103">Este elemento de configuração é usado para especificar o comportamento de tempo de execução para receber mensagens em um serviço ou aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="dee1e-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="dee1e-104">Ele não tem nenhum atributo ou elemento filho.</span><span class="sxs-lookup"><span data-stu-id="dee1e-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="dee1e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dee1e-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dee1e-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dee1e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="dee1e-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dee1e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dee1e-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="dee1e-108">Attributes</span></span>  
 <span data-ttu-id="dee1e-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dee1e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dee1e-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dee1e-110">Child Elements</span></span>  
 <span data-ttu-id="dee1e-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dee1e-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dee1e-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dee1e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="dee1e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="dee1e-113">Element</span></span>|<span data-ttu-id="dee1e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee1e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dee1e-115">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dee1e-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dee1e-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="dee1e-116">Remarks</span></span>  
 <span data-ttu-id="dee1e-117">Use esse comportamento para instruir o ouvinte de canal a usar um recebimento síncrono, em vez do padrão, assíncrono.</span><span class="sxs-lookup"><span data-stu-id="dee1e-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="dee1e-118">Windows Communication Foundation (WCF) emite um novo thread para bombeamento para cada canal aceito.</span><span class="sxs-lookup"><span data-stu-id="dee1e-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="dee1e-119">Se houver muitos canais, haverá a possibilidade de ficar sem threads.</span><span class="sxs-lookup"><span data-stu-id="dee1e-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee1e-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="dee1e-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
