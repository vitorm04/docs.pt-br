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
ms.openlocfilehash: 9e228cfbdade420c4d5248ffd417c6131083ee74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110411"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="d6c8a-102">Enumeração COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="d6c8a-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="d6c8a-103">Especifica as estatísticas sejam registradas para uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d6c8a-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c8a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6c8a-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="d6c8a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6c8a-105">Remarks</span></span>  
 <span data-ttu-id="d6c8a-106">Esta enumeração Especifica quais estatísticas na [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) estrutura devem ser definidas [iclrgcmanager:: getStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="d6c8a-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="d6c8a-107">Membros</span><span class="sxs-lookup"><span data-stu-id="d6c8a-107">Members</span></span>  
  
|<span data-ttu-id="d6c8a-108">Membro</span><span class="sxs-lookup"><span data-stu-id="d6c8a-108">Member</span></span>|<span data-ttu-id="d6c8a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6c8a-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="d6c8a-110">Registra o número de coletas de lixo executadas para cada geração.</span><span class="sxs-lookup"><span data-stu-id="d6c8a-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="d6c8a-111">Registros memória lixo e uso coleta estatísticas de tamanho.</span><span class="sxs-lookup"><span data-stu-id="d6c8a-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6c8a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6c8a-112">Requirements</span></span>  
 <span data-ttu-id="d6c8a-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6c8a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c8a-114">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="d6c8a-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 **<span data-ttu-id="d6c8a-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d6c8a-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d6c8a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6c8a-116">See also</span></span>

- [<span data-ttu-id="d6c8a-117">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="d6c8a-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="d6c8a-118">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="d6c8a-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
