---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 269500324ad1beaa0b519fa17d251ee942276faa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269062"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="abd4c-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="abd4c-101">\<callbackTimeouts></span></span>
<span data-ttu-id="abd4c-102">Especifica o valor de tempo limite ao fluir transações de servidor para chmada um cenário de contrato de retorno de chamada duplex.</span><span class="sxs-lookup"><span data-stu-id="abd4c-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="abd4c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="abd4c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="abd4c-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="abd4c-104">\<behaviors></span></span>  
<span data-ttu-id="abd4c-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="abd4c-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="abd4c-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="abd4c-106">\<behavior></span></span>  
<span data-ttu-id="abd4c-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="abd4c-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abd4c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abd4c-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="abd4c-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="abd4c-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abd4c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="abd4c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="abd4c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="abd4c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abd4c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="abd4c-112">Attributes</span></span>  
  
|<span data-ttu-id="abd4c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="abd4c-113">Attribute</span></span>|<span data-ttu-id="abd4c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="abd4c-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="abd4c-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo em que as transações devem ser concluídas ou automaticamente encerrada.</span><span class="sxs-lookup"><span data-stu-id="abd4c-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="abd4c-116">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="abd4c-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abd4c-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="abd4c-117">Child Elements</span></span>  
 <span data-ttu-id="abd4c-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="abd4c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abd4c-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="abd4c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="abd4c-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="abd4c-120">Element</span></span>|<span data-ttu-id="abd4c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="abd4c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abd4c-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="abd4c-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="abd4c-123">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="abd4c-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abd4c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abd4c-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
