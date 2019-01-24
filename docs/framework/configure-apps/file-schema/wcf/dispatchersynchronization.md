---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 537dee408f1af29a06042de439a2c1e7d7874222
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555382"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="b5981-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="b5981-102">&lt;dispatcherSynchronization&gt;</span></span>
  
<span data-ttu-id="b5981-103">Especifica um comportamento de ponto de extremidade que habilita um serviço enviar respostas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="b5981-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="b5981-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b5981-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b5981-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b5981-105">\<behaviors></span></span>  
<span data-ttu-id="b5981-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b5981-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="b5981-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b5981-107">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5981-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5981-108">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="b5981-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="b5981-109">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5981-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b5981-110">Attributes and elements</span></span>  
  
<span data-ttu-id="b5981-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b5981-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5981-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b5981-112">Attributes</span></span>

| <span data-ttu-id="b5981-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b5981-113">Attribute</span></span>               | <span data-ttu-id="b5981-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5981-114">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="b5981-115">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="b5981-115">asynchronousSendEnabled</span></span> | <span data-ttu-id="b5981-116">Um booliano que especifica se o comportamento de envio assíncrono está habilitado.</span><span class="sxs-lookup"><span data-stu-id="b5981-116">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="b5981-117">Um inteiro que especifica que o número de recebimentos concorrentes que pode ser emitido no canal.</span><span class="sxs-lookup"><span data-stu-id="b5981-117">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="b5981-118">Esse valor deve ser configurado somente depois que você configurou corretamente o comportamento de limitação do serviço.</span><span class="sxs-lookup"><span data-stu-id="b5981-118">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="b5981-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b5981-119">Child elements</span></span>

<span data-ttu-id="b5981-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b5981-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5981-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b5981-121">Parent elements</span></span>

| <span data-ttu-id="b5981-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5981-122">Element</span></span> | <span data-ttu-id="b5981-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5981-123">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="b5981-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b5981-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b5981-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b5981-125">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b5981-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5981-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
