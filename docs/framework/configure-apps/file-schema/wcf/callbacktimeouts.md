---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: d57a888a19e684ac13632c1ab2476e304667c3e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919661"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="dbf34-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="dbf34-101">\<callbackTimeouts></span></span>
<span data-ttu-id="dbf34-102">Especifica o valor de tempo limite ao fluir transações do servidor para client.in um cenário de contrato de retorno de chamada duplex.</span><span class="sxs-lookup"><span data-stu-id="dbf34-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="dbf34-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dbf34-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="dbf34-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="dbf34-104">\<behaviors></span></span>  
<span data-ttu-id="dbf34-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="dbf34-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="dbf34-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dbf34-106">\<behavior></span></span>  
<span data-ttu-id="dbf34-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="dbf34-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbf34-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbf34-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="dbf34-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="dbf34-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbf34-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dbf34-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dbf34-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dbf34-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbf34-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="dbf34-112">Attributes</span></span>  
  
|<span data-ttu-id="dbf34-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="dbf34-113">Attribute</span></span>|<span data-ttu-id="dbf34-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbf34-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="dbf34-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo dentro do qual as transações devem ser concluídas ou encerradas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="dbf34-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="dbf34-116">O padrão é "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="dbf34-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbf34-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dbf34-117">Child Elements</span></span>  
 <span data-ttu-id="dbf34-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dbf34-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbf34-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dbf34-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dbf34-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="dbf34-120">Element</span></span>|<span data-ttu-id="dbf34-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbf34-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbf34-122">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dbf34-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dbf34-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dbf34-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbf34-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbf34-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
