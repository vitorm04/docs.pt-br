---
title: '&lt;callbackTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e86b69b7d633fd99728936070e94da964e16de58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="63290-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="63290-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="63290-103">Especifica o valor de tempo limite ao fluir transações de servidor para chmada um cenário de contrato de retorno de chamada dúplex.</span><span class="sxs-lookup"><span data-stu-id="63290-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="63290-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="63290-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63290-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="63290-105">\<behaviors></span></span>  
<span data-ttu-id="63290-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="63290-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="63290-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="63290-107">\<behavior></span></span>  
<span data-ttu-id="63290-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="63290-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63290-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63290-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="63290-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="63290-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63290-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="63290-111">Attributes and Elements</span></span>  
 <span data-ttu-id="63290-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="63290-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63290-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="63290-113">Attributes</span></span>  
  
|<span data-ttu-id="63290-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="63290-114">Attribute</span></span>|<span data-ttu-id="63290-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="63290-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="63290-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo em que as transações devem ser completadas ou automaticamente encerrada.</span><span class="sxs-lookup"><span data-stu-id="63290-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="63290-117">O padrão é "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="63290-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63290-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="63290-118">Child Elements</span></span>  
 <span data-ttu-id="63290-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="63290-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63290-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="63290-120">Parent Elements</span></span>  
  
|<span data-ttu-id="63290-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="63290-121">Element</span></span>|<span data-ttu-id="63290-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="63290-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63290-123">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="63290-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="63290-124">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="63290-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63290-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63290-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
