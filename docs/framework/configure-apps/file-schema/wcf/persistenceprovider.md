---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 054991687a54ecbf95cc18f58717a4ed3e36f050
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260795"
---
# <a name="persistenceprovider"></a><span data-ttu-id="db30a-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="db30a-101">\<persistenceProvider></span></span>
<span data-ttu-id="db30a-102">Especifica o tipo de implementação do provedor de persistência a usar, bem como o tempo limite a ser usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="db30a-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="db30a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="db30a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="db30a-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="db30a-104">\<behaviors></span></span>  
<span data-ttu-id="db30a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="db30a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="db30a-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="db30a-106">\<behavior></span></span>  
<span data-ttu-id="db30a-107">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="db30a-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db30a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db30a-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db30a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="db30a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="db30a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="db30a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db30a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="db30a-111">Attributes</span></span>  
  
|<span data-ttu-id="db30a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="db30a-112">Attribute</span></span>|<span data-ttu-id="db30a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="db30a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db30a-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="db30a-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="db30a-115">Um <xref:System.TimeSpan> valor que especifica o tempo limite usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="db30a-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="db30a-116">O padrão é "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="db30a-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="db30a-117">tipo</span><span class="sxs-lookup"><span data-stu-id="db30a-117">type</span></span>|<span data-ttu-id="db30a-118">Uma cadeia de caracteres que especifica o tipo da fábrica de provedor de persistência a usar.</span><span class="sxs-lookup"><span data-stu-id="db30a-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db30a-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="db30a-119">Child Elements</span></span>  
 <span data-ttu-id="db30a-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="db30a-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db30a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="db30a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="db30a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="db30a-122">Element</span></span>|<span data-ttu-id="db30a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="db30a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db30a-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="db30a-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="db30a-125">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="db30a-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db30a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="db30a-126">Remarks</span></span>  
 <span data-ttu-id="db30a-127">Esse elemento Especifica o provedor de persistência a ser usado para serializar o estado de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="db30a-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="db30a-128">Ele deve ser usado junto com o `wsHttpContextBinding` que passa informações de estado em cabeçalhos HTTP.</span><span class="sxs-lookup"><span data-stu-id="db30a-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db30a-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db30a-129">See also</span></span>
- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
