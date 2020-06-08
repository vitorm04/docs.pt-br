---
title: Enumeração COR_GC_STAT_TYPES
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: d7e78dfc4beba67cc376b221d0cd49f7200f5d23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501684"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="4a91f-102">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="4a91f-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="4a91f-103">Especifica as estatísticas a serem registradas para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4a91f-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a91f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a91f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="4a91f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a91f-105">Remarks</span></span>  
 <span data-ttu-id="4a91f-106">Essa enumeração Especifica quais estatísticas na estrutura de [COR_GC_STATS](cor-gc-stats-structure.md) devem ser definidas pelo método [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4a91f-106">This enumeration specifies which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="4a91f-107">Membros</span><span class="sxs-lookup"><span data-stu-id="4a91f-107">Members</span></span>  
  
|<span data-ttu-id="4a91f-108">Membro</span><span class="sxs-lookup"><span data-stu-id="4a91f-108">Member</span></span>|<span data-ttu-id="4a91f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a91f-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="4a91f-110">Registra o número de coletas de lixo executadas para cada geração.</span><span class="sxs-lookup"><span data-stu-id="4a91f-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="4a91f-111">Registra o uso de memória e estatísticas de tamanho da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4a91f-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a91f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a91f-112">Requirements</span></span>  
 <span data-ttu-id="4a91f-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a91f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a91f-114">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="4a91f-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="4a91f-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a91f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a91f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="4a91f-116">See also</span></span>

- [<span data-ttu-id="4a91f-117">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="4a91f-117">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="4a91f-118">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="4a91f-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
