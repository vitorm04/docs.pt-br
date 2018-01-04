---
title: "Enumeração COR_GC_STAT_TYPES"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STAT_TYPES
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STAT_TYPES
helpviewer_keywords: COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86d0ce931518fa50dbd3b0d6d7f2755d19042eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="c3710-102">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="c3710-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="c3710-103">Especifica as estatísticas sejam registradas para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c3710-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3710-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3710-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="c3710-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3710-105">Remarks</span></span>  
 <span data-ttu-id="c3710-106">Esta enumeração Especifica quais estatísticas no [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) estrutura devem ser definidas [Iclrgcmanager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c3710-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="c3710-107">Membros</span><span class="sxs-lookup"><span data-stu-id="c3710-107">Members</span></span>  
  
|<span data-ttu-id="c3710-108">Membro</span><span class="sxs-lookup"><span data-stu-id="c3710-108">Member</span></span>|<span data-ttu-id="c3710-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3710-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="c3710-110">Registra o número de coletas de lixo executadas para cada geração.</span><span class="sxs-lookup"><span data-stu-id="c3710-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="c3710-111">Registros memória uso e lixo coleta as estatísticas de tamanho.</span><span class="sxs-lookup"><span data-stu-id="c3710-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3710-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3710-112">Requirements</span></span>  
 <span data-ttu-id="c3710-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3710-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3710-114">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="c3710-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c3710-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3710-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3710-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3710-116">See Also</span></span>  
 [<span data-ttu-id="c3710-117">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="c3710-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="c3710-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="c3710-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
