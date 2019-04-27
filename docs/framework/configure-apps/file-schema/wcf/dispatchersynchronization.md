---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673401"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="f456d-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="f456d-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="f456d-102">Especifica um comportamento de ponto de extremidade que habilita um serviço enviar respostas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="f456d-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="f456d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f456d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f456d-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f456d-104">\<behaviors></span></span>  
<span data-ttu-id="f456d-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f456d-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="f456d-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f456d-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f456d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f456d-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f456d-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="f456d-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f456d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f456d-109">Attributes and elements</span></span>  
  
<span data-ttu-id="f456d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f456d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f456d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f456d-111">Attributes</span></span>

| <span data-ttu-id="f456d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f456d-112">Attribute</span></span>               | <span data-ttu-id="f456d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f456d-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="f456d-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="f456d-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="f456d-115">Um booliano que especifica se o comportamento de envio assíncrono está habilitado.</span><span class="sxs-lookup"><span data-stu-id="f456d-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="f456d-116">Um inteiro que especifica que o número de recebimentos concorrentes que pode ser emitido no canal.</span><span class="sxs-lookup"><span data-stu-id="f456d-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="f456d-117">Esse valor deve ser configurado somente depois que você configurou corretamente o comportamento de limitação do serviço.</span><span class="sxs-lookup"><span data-stu-id="f456d-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f456d-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f456d-118">Child elements</span></span>

<span data-ttu-id="f456d-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f456d-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f456d-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f456d-120">Parent elements</span></span>

| <span data-ttu-id="f456d-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f456d-121">Element</span></span> | <span data-ttu-id="f456d-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f456d-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="f456d-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f456d-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f456d-124">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f456d-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f456d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f456d-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
