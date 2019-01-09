---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 86660620113b162a9a5260b7026a64455284d184
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151456"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="f62e5-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="f62e5-102">&lt;dispatcherSynchronization&gt;</span></span>
  
<span data-ttu-id="f62e5-103">Especifica um comportamento de ponto de extremidade que habilita um serviço enviar respostas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="f62e5-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="f62e5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f62e5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f62e5-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f62e5-105">\<behaviors></span></span>  
<span data-ttu-id="f62e5-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f62e5-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f62e5-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="f62e5-107">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f62e5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f62e5-108">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f62e5-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="f62e5-109">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f62e5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f62e5-110">Attributes and elements</span></span>  
  
<span data-ttu-id="f62e5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f62e5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f62e5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f62e5-112">Attributes</span></span>

| <span data-ttu-id="f62e5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f62e5-113">Attribute</span></span>               | <span data-ttu-id="f62e5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f62e5-114">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="f62e5-115">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="f62e5-115">asynchronousSendEnabled</span></span> | <span data-ttu-id="f62e5-116">Um booliano que especifica se o comportamento de envio assíncrono está habilitado.</span><span class="sxs-lookup"><span data-stu-id="f62e5-116">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="f62e5-117">Um inteiro que especifica que o número de recebimentos concorrentes que pode ser emitido no canal.</span><span class="sxs-lookup"><span data-stu-id="f62e5-117">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="f62e5-118">Esse valor deve ser configurado somente depois que você configurou corretamente o comportamento de limitação do serviço.</span><span class="sxs-lookup"><span data-stu-id="f62e5-118">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f62e5-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f62e5-119">Child elements</span></span>

<span data-ttu-id="f62e5-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f62e5-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f62e5-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f62e5-121">Parent elements</span></span>

| <span data-ttu-id="f62e5-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f62e5-122">Element</span></span> | <span data-ttu-id="f62e5-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f62e5-123">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="f62e5-124">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="f62e5-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f62e5-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f62e5-125">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f62e5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f62e5-126">See also</span></span>

 <span data-ttu-id="f62e5-127"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="f62e5-127"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
