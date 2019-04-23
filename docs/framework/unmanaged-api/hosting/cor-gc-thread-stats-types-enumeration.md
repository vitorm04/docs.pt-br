---
title: Enumeração COR_GC_THREAD_STATS_TYPES
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c631a0a3abb3cb2a342dfd44fdffb147b742ae3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212460"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="c6131-102">Enumeração COR_GC_THREAD_STATS_TYPES</span><span class="sxs-lookup"><span data-stu-id="c6131-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="c6131-103">Indica as estatísticas de coleta de lixo para um thread.</span><span class="sxs-lookup"><span data-stu-id="c6131-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6131-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6131-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="c6131-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c6131-105">Members</span></span>  
  
|<span data-ttu-id="c6131-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c6131-106">Member</span></span>|<span data-ttu-id="c6131-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6131-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="c6131-108">O thread tiver de bytes que foram promovidos na coleta de lixo a mais recente.</span><span class="sxs-lookup"><span data-stu-id="c6131-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6131-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6131-109">Requirements</span></span>  
 <span data-ttu-id="c6131-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6131-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6131-111">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="c6131-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c6131-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6131-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6131-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6131-113">See also</span></span>

- [<span data-ttu-id="c6131-114">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="c6131-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
