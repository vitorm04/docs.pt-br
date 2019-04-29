---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dc8dea0ddd1ea074c08952e3e2ebfef2d12f7183
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783286"
---
# <a name="persistenceprovider"></a><span data-ttu-id="d8fec-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="d8fec-101">\<persistenceProvider></span></span>
<span data-ttu-id="d8fec-102">Especifica o tipo de implementação do provedor de persistência a usar, bem como o tempo limite a ser usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="d8fec-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="d8fec-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d8fec-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d8fec-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d8fec-104">\<behaviors></span></span>  
<span data-ttu-id="d8fec-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d8fec-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="d8fec-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d8fec-106">\<behavior></span></span>  
<span data-ttu-id="d8fec-107">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="d8fec-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8fec-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8fec-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8fec-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d8fec-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d8fec-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d8fec-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8fec-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d8fec-111">Attributes</span></span>  
  
|<span data-ttu-id="d8fec-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="d8fec-112">Attribute</span></span>|<span data-ttu-id="d8fec-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8fec-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8fec-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="d8fec-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="d8fec-115">Um <xref:System.TimeSpan> valor que especifica o tempo limite usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="d8fec-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="d8fec-116">O padrão é "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="d8fec-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="d8fec-117">tipo</span><span class="sxs-lookup"><span data-stu-id="d8fec-117">type</span></span>|<span data-ttu-id="d8fec-118">Uma cadeia de caracteres que especifica o tipo da fábrica de provedor de persistência a usar.</span><span class="sxs-lookup"><span data-stu-id="d8fec-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8fec-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d8fec-119">Child Elements</span></span>  
 <span data-ttu-id="d8fec-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d8fec-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8fec-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d8fec-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d8fec-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8fec-122">Element</span></span>|<span data-ttu-id="d8fec-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8fec-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8fec-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d8fec-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d8fec-125">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="d8fec-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8fec-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8fec-126">Remarks</span></span>  
 <span data-ttu-id="d8fec-127">Esse elemento Especifica o provedor de persistência a ser usado para serializar o estado de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="d8fec-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="d8fec-128">Ele deve ser usado junto com o `wsHttpContextBinding` que passa informações de estado em cabeçalhos HTTP.</span><span class="sxs-lookup"><span data-stu-id="d8fec-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fec-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8fec-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
