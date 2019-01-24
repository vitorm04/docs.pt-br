---
title: Estrutura COR_GC_STATS
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fc212321b28545f62f0a1c2965281d02ac73e40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638100"
---
# <a name="corgcstats-structure"></a><span data-ttu-id="fa58e-102">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="fa58e-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="fa58e-103">Fornece estatísticas sobre o mecanismo de coleta de lixo do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fa58e-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa58e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa58e-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="fa58e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fa58e-105">Members</span></span>  
  
|<span data-ttu-id="fa58e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fa58e-106">Member</span></span>|<span data-ttu-id="fa58e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa58e-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="fa58e-108">Indica quais valores do campo devem ser calculados e retornados.</span><span class="sxs-lookup"><span data-stu-id="fa58e-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="fa58e-109">Indica o número de coletas de lixo que foram forçados por solicitação externa.</span><span class="sxs-lookup"><span data-stu-id="fa58e-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="fa58e-110">Indica o número de coletas de lixo executadas para cada geração.</span><span class="sxs-lookup"><span data-stu-id="fa58e-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="fa58e-111">O número total de quilobytes confirmada em todos os heaps.</span><span class="sxs-lookup"><span data-stu-id="fa58e-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="fa58e-112">O número total de quilobytes reservado em todos os heaps.</span><span class="sxs-lookup"><span data-stu-id="fa58e-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="fa58e-113">O tamanho, em quilobytes, do heap de geração de zero.</span><span class="sxs-lookup"><span data-stu-id="fa58e-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="fa58e-114">O tamanho, em quilobytes, da geração de um heap.</span><span class="sxs-lookup"><span data-stu-id="fa58e-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="fa58e-115">O tamanho, em quilobytes, do heap de geração 2.</span><span class="sxs-lookup"><span data-stu-id="fa58e-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="fa58e-116">O tamanho, em quilobytes, do heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="fa58e-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="fa58e-117">O tamanho, em quilobytes, dos objetos promovidos da geração de zero para geração de um.</span><span class="sxs-lookup"><span data-stu-id="fa58e-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="fa58e-118">O tamanho, em quilobytes, dos objetos promovidos da geração de um para geração de dois.</span><span class="sxs-lookup"><span data-stu-id="fa58e-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa58e-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa58e-119">Remarks</span></span>  
 <span data-ttu-id="fa58e-120">O [iclrgcmanager:: getStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) método requer que o `Flags` campo dos `COR_GC_STATS` estrutura a ser definido para um ou mais valores da [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeração para especificar quais as estatísticas devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="fa58e-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="fa58e-121">A tabela a seguir mapeia as estatísticas fornecidas por essa estrutura para os dois [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) valores de enumeração `COR_GC_COUNTS` e `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="fa58e-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="fa58e-122">Especificado pelo COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="fa58e-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="fa58e-123">Especificado pelo COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="fa58e-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="fa58e-124">Um exemplo do uso é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fa58e-124">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fa58e-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa58e-125">Requirements</span></span>  
 <span data-ttu-id="fa58e-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa58e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa58e-127">**Cabeçalho:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="fa58e-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="fa58e-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fa58e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa58e-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa58e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa58e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa58e-130">See also</span></span>
- [<span data-ttu-id="fa58e-131">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="fa58e-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="fa58e-132">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="fa58e-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="fa58e-133">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="fa58e-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
