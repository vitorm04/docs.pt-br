---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a1792fec4f86c9ac31107c043b976cfafcfa4c13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937088"
---
# <a name="servicetimeouts"></a><span data-ttu-id="c098e-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="c098e-101">\<serviceTimeouts></span></span>
<span data-ttu-id="c098e-102">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="c098e-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="c098e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c098e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c098e-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="c098e-104">\<behaviors></span></span>  
<span data-ttu-id="c098e-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="c098e-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c098e-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="c098e-106">\<behavior></span></span>  
<span data-ttu-id="c098e-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="c098e-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c098e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c098e-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="c098e-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="c098e-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c098e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c098e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c098e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c098e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c098e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c098e-112">Attributes</span></span>  
  
|<span data-ttu-id="c098e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c098e-113">Attribute</span></span>|<span data-ttu-id="c098e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c098e-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="c098e-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo que uma transação deve fluir do cliente para o servidor.</span><span class="sxs-lookup"><span data-stu-id="c098e-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="c098e-116">O padrão é "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="c098e-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c098e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c098e-117">Child Elements</span></span>  
 <span data-ttu-id="c098e-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c098e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c098e-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c098e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c098e-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="c098e-120">Element</span></span>|<span data-ttu-id="c098e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c098e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c098e-122">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="c098e-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c098e-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="c098e-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c098e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c098e-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
