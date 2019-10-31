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
ms.openlocfilehash: 63275aaa7ed1f63c4f100845d2cbe9e93fcd0bcd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131249"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="d6f76-102">Enumeração COR_GC_THREAD_STATS_TYPES</span><span class="sxs-lookup"><span data-stu-id="d6f76-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="d6f76-103">Indica as estatísticas de coleta de lixo para um thread.</span><span class="sxs-lookup"><span data-stu-id="d6f76-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6f76-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6f76-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="d6f76-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d6f76-105">Members</span></span>  
  
|<span data-ttu-id="d6f76-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d6f76-106">Member</span></span>|<span data-ttu-id="d6f76-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6f76-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="d6f76-108">O thread tem bytes que foram promovidos na coleta de lixo mais recente.</span><span class="sxs-lookup"><span data-stu-id="d6f76-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6f76-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6f76-109">Requirements</span></span>  
 <span data-ttu-id="d6f76-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6f76-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6f76-111">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="d6f76-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d6f76-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6f76-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f76-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6f76-113">See also</span></span>

- [<span data-ttu-id="d6f76-114">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d6f76-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
