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
ms.openlocfilehash: 2206499cad9be2a29f485ee66d468accbe00b5f5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616663"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="ce79c-102">Enumeração COR_GC_THREAD_STATS_TYPES</span><span class="sxs-lookup"><span data-stu-id="ce79c-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="ce79c-103">Indica as estatísticas de coleta de lixo para um thread.</span><span class="sxs-lookup"><span data-stu-id="ce79c-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce79c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce79c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="ce79c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ce79c-105">Members</span></span>  
  
|<span data-ttu-id="ce79c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ce79c-106">Member</span></span>|<span data-ttu-id="ce79c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce79c-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="ce79c-108">O thread tem bytes que foram promovidos na coleta de lixo mais recente.</span><span class="sxs-lookup"><span data-stu-id="ce79c-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce79c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce79c-109">Requirements</span></span>  
 <span data-ttu-id="ce79c-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce79c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce79c-111">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="ce79c-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ce79c-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce79c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce79c-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="ce79c-113">See also</span></span>

- [<span data-ttu-id="ce79c-114">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="ce79c-114">Hosting Enumerations</span></span>](hosting-enumerations.md)
