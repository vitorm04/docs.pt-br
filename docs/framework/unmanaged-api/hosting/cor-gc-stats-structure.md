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
ms.openlocfilehash: 12c00ed009e0e57436a71aed256b07a58ba68a32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138342"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="37916-102">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="37916-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="37916-103">Fornece estatísticas sobre o mecanismo de coleta de lixo do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="37916-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37916-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37916-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="37916-105">Membros</span><span class="sxs-lookup"><span data-stu-id="37916-105">Members</span></span>  
  
|<span data-ttu-id="37916-106">Membro</span><span class="sxs-lookup"><span data-stu-id="37916-106">Member</span></span>|<span data-ttu-id="37916-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="37916-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="37916-108">Indica quais valores de campo devem ser calculados e retornados.</span><span class="sxs-lookup"><span data-stu-id="37916-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="37916-109">Indica o número de coletas de lixo que foram forçadas por solicitação externa.</span><span class="sxs-lookup"><span data-stu-id="37916-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="37916-110">Indica o número de coletas de lixo executadas para cada geração.</span><span class="sxs-lookup"><span data-stu-id="37916-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="37916-111">O número total de quilobytes confirmados em todos os heaps.</span><span class="sxs-lookup"><span data-stu-id="37916-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="37916-112">O número total de kilobytes reservados em todos os heaps.</span><span class="sxs-lookup"><span data-stu-id="37916-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="37916-113">O tamanho, em quilobytes, do heap de geração-zero.</span><span class="sxs-lookup"><span data-stu-id="37916-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="37916-114">O tamanho, em quilobytes, do heap de geração-um.</span><span class="sxs-lookup"><span data-stu-id="37916-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="37916-115">O tamanho, em quilobytes, do heap de geração-dois.</span><span class="sxs-lookup"><span data-stu-id="37916-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="37916-116">O tamanho, em quilobytes, do heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="37916-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="37916-117">O tamanho, em quilobytes, dos objetos promovidos da geração zero para a geração um.</span><span class="sxs-lookup"><span data-stu-id="37916-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="37916-118">O tamanho, em quilobytes, dos objetos promovidos da geração um para a geração dois.</span><span class="sxs-lookup"><span data-stu-id="37916-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37916-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="37916-119">Remarks</span></span>  
 <span data-ttu-id="37916-120">O método [ICLRGCManager:: GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) exige que o campo `Flags` da estrutura de `COR_GC_STATS` seja definida como um ou mais valores da enumeração [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) para especificar quais estatísticas devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="37916-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="37916-121">A tabela a seguir mapeia as estatísticas fornecidas por essa estrutura para os dois valores de enumeração [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) , `COR_GC_COUNTS` e `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="37916-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="37916-122">Especificado por COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="37916-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="37916-123">Especificado por COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="37916-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="37916-124">Um exemplo de uso é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="37916-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="37916-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37916-125">Requirements</span></span>  
 <span data-ttu-id="37916-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37916-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37916-127">**Cabeçalho:** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="37916-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="37916-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37916-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37916-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37916-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37916-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37916-130">See also</span></span>

- [<span data-ttu-id="37916-131">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="37916-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="37916-132">Gerenciamento Automático de Memória</span><span class="sxs-lookup"><span data-stu-id="37916-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="37916-133">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="37916-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
