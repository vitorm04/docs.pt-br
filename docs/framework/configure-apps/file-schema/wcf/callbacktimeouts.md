---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 01932fe2b7b7e699311e2c65ec8adaf0aef82dc5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557897"
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="63609-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="63609-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="63609-103">Especifica o valor de tempo limite ao fluir transações de servidor para chmada um cenário de contrato de retorno de chamada duplex.</span><span class="sxs-lookup"><span data-stu-id="63609-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="63609-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63609-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63609-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="63609-105">\<behaviors></span></span>  
<span data-ttu-id="63609-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="63609-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="63609-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="63609-107">\<behavior></span></span>  
<span data-ttu-id="63609-108">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="63609-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63609-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63609-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="63609-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="63609-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63609-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="63609-111">Attributes and Elements</span></span>  
 <span data-ttu-id="63609-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="63609-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63609-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="63609-113">Attributes</span></span>  
  
|<span data-ttu-id="63609-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="63609-114">Attribute</span></span>|<span data-ttu-id="63609-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="63609-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="63609-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo em que as transações devem ser concluídas ou automaticamente encerrada.</span><span class="sxs-lookup"><span data-stu-id="63609-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="63609-117">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="63609-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63609-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="63609-118">Child Elements</span></span>  
 <span data-ttu-id="63609-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="63609-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63609-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="63609-120">Parent Elements</span></span>  
  
|<span data-ttu-id="63609-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="63609-121">Element</span></span>|<span data-ttu-id="63609-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="63609-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63609-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="63609-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="63609-124">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="63609-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63609-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63609-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
