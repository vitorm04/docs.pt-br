---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 3c7fd74a84184ddbf8cc8db90141174ed84e5774
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="eea9a-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="eea9a-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="eea9a-103">Especifica o tipo de implementação do provedor de persistência a ser usado, bem como o tempo limite a ser usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="eea9a-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="eea9a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eea9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="eea9a-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="eea9a-105">\<behaviors></span></span>  
<span data-ttu-id="eea9a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="eea9a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="eea9a-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="eea9a-107">\<behavior></span></span>  
<span data-ttu-id="eea9a-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="eea9a-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea9a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eea9a-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eea9a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eea9a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eea9a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eea9a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eea9a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="eea9a-112">Attributes</span></span>  
  
|<span data-ttu-id="eea9a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="eea9a-113">Attribute</span></span>|<span data-ttu-id="eea9a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="eea9a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eea9a-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="eea9a-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="eea9a-116">Um <xref:System.TimeSpan> valor que especifica o tempo limite usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="eea9a-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="eea9a-117">O padrão é "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="eea9a-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="eea9a-118">tipo</span><span class="sxs-lookup"><span data-stu-id="eea9a-118">type</span></span>|<span data-ttu-id="eea9a-119">Uma cadeia de caracteres que especifica o tipo de fábrica do provedor de persistência para usar.</span><span class="sxs-lookup"><span data-stu-id="eea9a-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eea9a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eea9a-120">Child Elements</span></span>  
 <span data-ttu-id="eea9a-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eea9a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eea9a-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eea9a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="eea9a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="eea9a-123">Element</span></span>|<span data-ttu-id="eea9a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="eea9a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eea9a-125">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="eea9a-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="eea9a-126">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="eea9a-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eea9a-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="eea9a-127">Remarks</span></span>  
 <span data-ttu-id="eea9a-128">Este elemento Especifica o provedor de persistência a ser usado para serializar o estado de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="eea9a-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="eea9a-129">Ele deve ser usado junto com o `wsHttpContextBinding` que passa informações de estado em cabeçalhos HTTP.</span><span class="sxs-lookup"><span data-stu-id="eea9a-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea9a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eea9a-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
