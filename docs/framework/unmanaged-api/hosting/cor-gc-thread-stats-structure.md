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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f56ceca5269ebffb29908c63e698ce794027d8a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768053"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="40e61-102">Estrutura COR_GC_THREAD_STATS</span><span class="sxs-lookup"><span data-stu-id="40e61-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="40e61-103">Contém estatísticas por thread referentes à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="40e61-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40e61-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="40e61-105">Membros</span><span class="sxs-lookup"><span data-stu-id="40e61-105">Members</span></span>  
  
|<span data-ttu-id="40e61-106">Membro</span><span class="sxs-lookup"><span data-stu-id="40e61-106">Member</span></span>|<span data-ttu-id="40e61-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="40e61-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="40e61-108">O número de bytes de memória alocada no thread que está associado com a atual `COR_GC_THREAD_STATS` instância.</span><span class="sxs-lookup"><span data-stu-id="40e61-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="40e61-109">Esse número será limpo com zero sempre que ocorre uma coleta de lixo de geração de zero.</span><span class="sxs-lookup"><span data-stu-id="40e61-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="40e61-110">O número de bytes promovidos para uma geração mais alta a coleta de lixo mais recentes.</span><span class="sxs-lookup"><span data-stu-id="40e61-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40e61-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="40e61-111">Remarks</span></span>  
 <span data-ttu-id="40e61-112">[Iclrtask:: Getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) aceita um parâmetro de saída do tipo `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="40e61-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40e61-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40e61-113">Requirements</span></span>  
 <span data-ttu-id="40e61-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40e61-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40e61-115">**Cabeçalho:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="40e61-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="40e61-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="40e61-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40e61-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40e61-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e61-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40e61-118">See also</span></span>

- [<span data-ttu-id="40e61-119">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="40e61-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="40e61-120">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="40e61-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
