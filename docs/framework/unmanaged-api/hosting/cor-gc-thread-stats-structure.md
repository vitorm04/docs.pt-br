---
title: Estrutura COR_GC_THREAD_STATS
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 37da471aaa8e9f802a8430d7b3289b375ff1b40a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136983"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="08883-102">Estrutura COR_GC_THREAD_STATS</span><span class="sxs-lookup"><span data-stu-id="08883-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="08883-103">Contém estatísticas por thread referentes à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="08883-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08883-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08883-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="08883-105">Membros</span><span class="sxs-lookup"><span data-stu-id="08883-105">Members</span></span>  
  
|<span data-ttu-id="08883-106">Membro</span><span class="sxs-lookup"><span data-stu-id="08883-106">Member</span></span>|<span data-ttu-id="08883-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="08883-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="08883-108">O número de bytes de memória alocados no thread que está associado à instância de `COR_GC_THREAD_STATS` atual.</span><span class="sxs-lookup"><span data-stu-id="08883-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="08883-109">Esse número é limpo para zero sempre que uma coleta de lixo de geração zero ocorre.</span><span class="sxs-lookup"><span data-stu-id="08883-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="08883-110">O número de bytes promovidos para uma geração mais alta na coleta de lixo mais recente.</span><span class="sxs-lookup"><span data-stu-id="08883-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08883-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="08883-111">Remarks</span></span>  
 <span data-ttu-id="08883-112">[ICLRTask:: GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) usa um parâmetro de saída do tipo `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="08883-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08883-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08883-113">Requirements</span></span>  
 <span data-ttu-id="08883-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08883-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08883-115">**Cabeçalho:** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="08883-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="08883-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08883-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08883-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08883-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08883-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08883-118">See also</span></span>

- [<span data-ttu-id="08883-119">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="08883-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="08883-120">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="08883-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
