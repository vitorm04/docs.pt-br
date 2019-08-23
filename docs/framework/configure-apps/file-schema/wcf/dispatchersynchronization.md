---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925852"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="32332-101">\<> dispatcherSynchronization</span><span class="sxs-lookup"><span data-stu-id="32332-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="32332-102">Especifica um comportamento de ponto de extremidade que permite que um serviço envie respostas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="32332-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="32332-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="32332-103">\<system.serviceModel></span></span>  
<span data-ttu-id="32332-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="32332-104">\<behaviors></span></span>  
<span data-ttu-id="32332-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="32332-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="32332-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="32332-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32332-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32332-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="32332-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="32332-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32332-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="32332-109">Attributes and elements</span></span>  
  
<span data-ttu-id="32332-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="32332-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32332-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="32332-111">Attributes</span></span>

| <span data-ttu-id="32332-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="32332-112">Attribute</span></span>               | <span data-ttu-id="32332-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="32332-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="32332-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="32332-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="32332-115">Um booliano que especifica se o comportamento de envio assíncrono está habilitado.</span><span class="sxs-lookup"><span data-stu-id="32332-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="32332-116">Um inteiro que especifica o número de recebimentos simultâneos que podem ser emitidos no canal.</span><span class="sxs-lookup"><span data-stu-id="32332-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="32332-117">Esse valor deve ser configurado somente depois que você tiver configurado corretamente o comportamento de limitação de serviço.</span><span class="sxs-lookup"><span data-stu-id="32332-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="32332-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="32332-118">Child elements</span></span>

<span data-ttu-id="32332-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="32332-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="32332-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="32332-120">Parent elements</span></span>

| <span data-ttu-id="32332-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="32332-121">Element</span></span> | <span data-ttu-id="32332-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="32332-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="32332-123">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="32332-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="32332-124">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="32332-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="32332-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32332-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
