---
title: '&lt;persistenceProvider&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b506b8ef14246ee954adb0a16102f4bb208106b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="481cb-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="481cb-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="481cb-103">Especifica o tipo de implementação do provedor de persistência a ser usado, bem como o tempo limite a ser usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="481cb-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="481cb-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="481cb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="481cb-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="481cb-105">\<behaviors></span></span>  
<span data-ttu-id="481cb-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="481cb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="481cb-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="481cb-107">\<behavior></span></span>  
<span data-ttu-id="481cb-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="481cb-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="481cb-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="481cb-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="481cb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="481cb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="481cb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="481cb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="481cb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="481cb-112">Attributes</span></span>  
  
|<span data-ttu-id="481cb-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="481cb-113">Attribute</span></span>|<span data-ttu-id="481cb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="481cb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="481cb-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="481cb-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="481cb-116">Um <xref:System.TimeSpan> valor que especifica o tempo limite usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="481cb-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="481cb-117">O padrão é "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="481cb-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="481cb-118">tipo</span><span class="sxs-lookup"><span data-stu-id="481cb-118">type</span></span>|<span data-ttu-id="481cb-119">Uma cadeia de caracteres que especifica o tipo de fábrica do provedor de persistência para usar.</span><span class="sxs-lookup"><span data-stu-id="481cb-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="481cb-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="481cb-120">Child Elements</span></span>  
 <span data-ttu-id="481cb-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="481cb-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="481cb-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="481cb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="481cb-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="481cb-123">Element</span></span>|<span data-ttu-id="481cb-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="481cb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="481cb-125">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="481cb-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="481cb-126">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="481cb-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="481cb-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="481cb-127">Remarks</span></span>  
 <span data-ttu-id="481cb-128">Este elemento Especifica o provedor de persistência a ser usado para serializar o estado de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="481cb-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="481cb-129">Ele deve ser usado junto com o `wsHttpContextBinding` que passa informações de estado em cabeçalhos HTTP.</span><span class="sxs-lookup"><span data-stu-id="481cb-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="481cb-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="481cb-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
