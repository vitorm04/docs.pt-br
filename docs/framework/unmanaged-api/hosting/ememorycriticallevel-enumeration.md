---
title: Enumeração EMemoryCriticalLevel
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 248f1d281697923e2da14517ca174fe615bba4ff
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616197"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="a2304-102">Enumeração EMemoryCriticalLevel</span><span class="sxs-lookup"><span data-stu-id="a2304-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="a2304-103">Contém valores que indicam o impacto de uma falha quando uma alocação de memória específica é solicitada, mas não pode ser satisfeita.</span><span class="sxs-lookup"><span data-stu-id="a2304-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2304-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2304-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="a2304-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a2304-105">Members</span></span>  
  
|<span data-ttu-id="a2304-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a2304-106">Member</span></span>|<span data-ttu-id="a2304-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2304-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="a2304-108">Indica que a alocação é essencial para executar código gerenciado no domínio que solicitou a alocação.</span><span class="sxs-lookup"><span data-stu-id="a2304-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="a2304-109">Se não for possível alocar memória, o CLR não poderá garantir que o domínio ainda seja utilizável.</span><span class="sxs-lookup"><span data-stu-id="a2304-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="a2304-110">O host decide a ação a ser tomada quando a alocação não puder ser satisfeita.</span><span class="sxs-lookup"><span data-stu-id="a2304-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="a2304-111">Ele pode instruir o CLR a anular o `AppDomain` automaticamente ou permitir que ele continue em execução chamando métodos em [ICLRPolicyManager](iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a2304-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="a2304-112">Indica que a alocação é essencial para a execução do código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="a2304-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="a2304-113">Esse valor é usado durante a inicialização e ao executar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="a2304-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="a2304-114">Se não for possível alocar memória, o CLR não poderá operar no processo.</span><span class="sxs-lookup"><span data-stu-id="a2304-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="a2304-115">Se a alocação falhar, o CLR será efetivamente desabilitado.</span><span class="sxs-lookup"><span data-stu-id="a2304-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="a2304-116">Todas as chamadas subsequentes para o CLR falham com HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a2304-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="a2304-117">Indica que a alocação é essencial para executar a tarefa que solicitou a alocação.</span><span class="sxs-lookup"><span data-stu-id="a2304-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="a2304-118">Se não for possível alocar memória, o CLR não poderá garantir que a tarefa possa ser executada.</span><span class="sxs-lookup"><span data-stu-id="a2304-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="a2304-119">Em caso de falha, o CLR gera um <xref:System.Threading.ThreadAbortException> no thread do sistema de operação física.</span><span class="sxs-lookup"><span data-stu-id="a2304-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2304-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2304-120">Remarks</span></span>  
 <span data-ttu-id="a2304-121">Os métodos de alocação de memória definidos nas interfaces [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) e [IHostMAlloc](ihostmalloc-interface.md) usam um parâmetro desse tipo.</span><span class="sxs-lookup"><span data-stu-id="a2304-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="a2304-122">Dependendo da severidade de uma falha, um host pode decidir se a solicitação de alocação deve falhar imediatamente ou aguardar até que possa ser satisfeita.</span><span class="sxs-lookup"><span data-stu-id="a2304-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2304-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2304-123">Requirements</span></span>  
 <span data-ttu-id="a2304-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2304-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2304-125">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a2304-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2304-126">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a2304-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2304-127">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2304-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2304-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="a2304-128">See also</span></span>

- [<span data-ttu-id="a2304-129">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="a2304-129">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="a2304-130">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="a2304-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
