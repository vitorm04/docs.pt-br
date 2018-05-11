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
ms.openlocfilehash: 74de8838d7f9ad1995bf7b15699b5589d13a0cab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="88802-102">Enumeração COR_GC_THREAD_STATS_TYPES</span><span class="sxs-lookup"><span data-stu-id="88802-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="88802-103">Indica as estatísticas de coleta de lixo para um thread.</span><span class="sxs-lookup"><span data-stu-id="88802-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88802-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88802-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="88802-105">Membros</span><span class="sxs-lookup"><span data-stu-id="88802-105">Members</span></span>  
  
|<span data-ttu-id="88802-106">Membro</span><span class="sxs-lookup"><span data-stu-id="88802-106">Member</span></span>|<span data-ttu-id="88802-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="88802-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="88802-108">O thread tem bytes que foram promovidas na coleta de lixo mais recente.</span><span class="sxs-lookup"><span data-stu-id="88802-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88802-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88802-109">Requirements</span></span>  
 <span data-ttu-id="88802-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88802-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88802-111">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="88802-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="88802-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88802-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88802-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88802-113">See Also</span></span>  
 [<span data-ttu-id="88802-114">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="88802-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
