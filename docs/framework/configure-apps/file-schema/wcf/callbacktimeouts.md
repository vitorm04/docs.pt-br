---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e666bac0be772e417f140e1482649f82ea70e2f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673414"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="7f51e-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="7f51e-101">\<callbackTimeouts></span></span>
<span data-ttu-id="7f51e-102">Especifica o valor de tempo limite ao fluir transações de servidor para chmada um cenário de contrato de retorno de chamada duplex.</span><span class="sxs-lookup"><span data-stu-id="7f51e-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="7f51e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7f51e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f51e-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7f51e-104">\<behaviors></span></span>  
<span data-ttu-id="7f51e-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7f51e-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="7f51e-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7f51e-106">\<behavior></span></span>  
<span data-ttu-id="7f51e-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="7f51e-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f51e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f51e-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="7f51e-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="7f51e-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f51e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7f51e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f51e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7f51e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f51e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7f51e-112">Attributes</span></span>  
  
|<span data-ttu-id="7f51e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="7f51e-113">Attribute</span></span>|<span data-ttu-id="7f51e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f51e-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="7f51e-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo em que as transações devem ser concluídas ou automaticamente encerrada.</span><span class="sxs-lookup"><span data-stu-id="7f51e-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="7f51e-116">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="7f51e-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f51e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7f51e-117">Child Elements</span></span>  
 <span data-ttu-id="7f51e-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7f51e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f51e-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7f51e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7f51e-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f51e-120">Element</span></span>|<span data-ttu-id="7f51e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f51e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f51e-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7f51e-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7f51e-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7f51e-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f51e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f51e-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
