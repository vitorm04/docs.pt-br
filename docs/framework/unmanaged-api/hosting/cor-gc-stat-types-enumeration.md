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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fdfe33c5b488d8f464001a86233124d4e7df0ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779074"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="5e52e-102">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="5e52e-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="5e52e-103">Especifica as estatísticas sejam registradas para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5e52e-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e52e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e52e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="5e52e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e52e-105">Remarks</span></span>  
 <span data-ttu-id="5e52e-106">Esta enumeração Especifica quais estatísticas na [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) estrutura devem ser definidas [iclrgcmanager:: getStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5e52e-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="5e52e-107">Membros</span><span class="sxs-lookup"><span data-stu-id="5e52e-107">Members</span></span>  
  
|<span data-ttu-id="5e52e-108">Membro</span><span class="sxs-lookup"><span data-stu-id="5e52e-108">Member</span></span>|<span data-ttu-id="5e52e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e52e-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="5e52e-110">Registra o número de coletas de lixo executadas para cada geração.</span><span class="sxs-lookup"><span data-stu-id="5e52e-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="5e52e-111">Registros memória lixo e uso coleta estatísticas de tamanho.</span><span class="sxs-lookup"><span data-stu-id="5e52e-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e52e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e52e-112">Requirements</span></span>  
 <span data-ttu-id="5e52e-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e52e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e52e-114">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="5e52e-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="5e52e-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e52e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e52e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e52e-116">See also</span></span>

- [<span data-ttu-id="5e52e-117">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="5e52e-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="5e52e-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5e52e-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
