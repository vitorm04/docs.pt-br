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
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176520"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="4fd78-102">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="4fd78-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="4fd78-103">Fornece estatísticas sobre o mecanismo de coleta de lixo do tempo de execução da linguagem comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="4fd78-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd78-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fd78-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4fd78-105">Membros</span><span class="sxs-lookup"><span data-stu-id="4fd78-105">Members</span></span>  
  
|<span data-ttu-id="4fd78-106">Membro</span><span class="sxs-lookup"><span data-stu-id="4fd78-106">Member</span></span>|<span data-ttu-id="4fd78-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4fd78-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="4fd78-108">Indica quais valores de campo devem ser calculados e devolvidos.</span><span class="sxs-lookup"><span data-stu-id="4fd78-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="4fd78-109">Indica o número de coletas de lixo que foram forçadas por solicitação externa.</span><span class="sxs-lookup"><span data-stu-id="4fd78-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="4fd78-110">Indica o número de coletas de lixo realizadas para cada geração.</span><span class="sxs-lookup"><span data-stu-id="4fd78-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="4fd78-111">O número total de kilobytes cometidos em todos os montes.</span><span class="sxs-lookup"><span data-stu-id="4fd78-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="4fd78-112">O número total de kilobytes reservados em todos os montes.</span><span class="sxs-lookup"><span data-stu-id="4fd78-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="4fd78-113">O tamanho, em kilobytes, da geração zero.</span><span class="sxs-lookup"><span data-stu-id="4fd78-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="4fd78-114">O tamanho, em kilobytes, da geração um pilha.</span><span class="sxs-lookup"><span data-stu-id="4fd78-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="4fd78-115">O tamanho, em kilobytes, da geração dois.</span><span class="sxs-lookup"><span data-stu-id="4fd78-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="4fd78-116">O tamanho, em kilobytes, do grande monte de objetos.</span><span class="sxs-lookup"><span data-stu-id="4fd78-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="4fd78-117">O tamanho, em kilobytes, dos objetos promovidos da geração zero à geração um.</span><span class="sxs-lookup"><span data-stu-id="4fd78-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="4fd78-118">O tamanho, em kilobytes, dos objetos promovidos da geração um à geração dois.</span><span class="sxs-lookup"><span data-stu-id="4fd78-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fd78-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fd78-119">Remarks</span></span>  
 <span data-ttu-id="4fd78-120">O método [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) exige `COR_GC_STATS` que o `Flags` campo da estrutura seja definido como um ou mais valores da enumeração [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) para especificar quais estatísticas devem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="4fd78-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="4fd78-121">A tabela a seguir mapeia as estatísticas fornecidas `COR_GC_COUNTS` por `COR_GC_MEMORYUSAGE`essa estrutura aos dois [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) valores de enumeração, e .</span><span class="sxs-lookup"><span data-stu-id="4fd78-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="4fd78-122">Especificado por COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="4fd78-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="4fd78-123">Especificado por COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="4fd78-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="4fd78-124">Um exemplo do uso é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4fd78-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4fd78-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4fd78-125">Requirements</span></span>  
 <span data-ttu-id="4fd78-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fd78-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fd78-127">**Cabeçalho:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="4fd78-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="4fd78-128">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fd78-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fd78-129">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fd78-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd78-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="4fd78-130">See also</span></span>

- [<span data-ttu-id="4fd78-131">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="4fd78-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="4fd78-132">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="4fd78-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="4fd78-133">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="4fd78-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
