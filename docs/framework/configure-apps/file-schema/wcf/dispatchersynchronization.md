---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398009"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="dc0c5-101">\<> dispatcherSynchronization</span><span class="sxs-lookup"><span data-stu-id="dc0c5-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="dc0c5-102">Especifica um comportamento de ponto de extremidade que permite que um serviço envie respostas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="dc0c5-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="dc0c5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dc0c5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dc0c5-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dc0c5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dc0c5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dc0c5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="dc0c5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dc0c5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="dc0c5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dc0c5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="dc0c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> dispatcherSynchronization**</span><span class="sxs-lookup"><span data-stu-id="dc0c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc0c5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc0c5-109">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="dc0c5-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="dc0c5-110">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc0c5-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dc0c5-111">Attributes and elements</span></span>  
  
<span data-ttu-id="dc0c5-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dc0c5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc0c5-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="dc0c5-113">Attributes</span></span>

| <span data-ttu-id="dc0c5-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="dc0c5-114">Attribute</span></span>               | <span data-ttu-id="dc0c5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc0c5-115">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="dc0c5-116">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="dc0c5-116">asynchronousSendEnabled</span></span> | <span data-ttu-id="dc0c5-117">Um booliano que especifica se o comportamento de envio assíncrono está habilitado.</span><span class="sxs-lookup"><span data-stu-id="dc0c5-117">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="dc0c5-118">Um inteiro que especifica o número de recebimentos simultâneos que podem ser emitidos no canal.</span><span class="sxs-lookup"><span data-stu-id="dc0c5-118">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="dc0c5-119">Esse valor deve ser configurado somente depois que você tiver configurado corretamente o comportamento de limitação de serviço.</span><span class="sxs-lookup"><span data-stu-id="dc0c5-119">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="dc0c5-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dc0c5-120">Child elements</span></span>

<span data-ttu-id="dc0c5-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dc0c5-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dc0c5-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dc0c5-122">Parent elements</span></span>

| <span data-ttu-id="dc0c5-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc0c5-123">Element</span></span> | <span data-ttu-id="dc0c5-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc0c5-124">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="dc0c5-125">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dc0c5-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dc0c5-126">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dc0c5-126">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="dc0c5-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc0c5-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
