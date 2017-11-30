---
title: "Enumeração EMemoryCriticalLevel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15a6786cb99a64d441d7e05fb91cd8ff0f3af92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="b0b38-102">Enumeração EMemoryCriticalLevel</span><span class="sxs-lookup"><span data-stu-id="b0b38-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="b0b38-103">Contém valores que indicam o impacto de uma falha quando uma alocação de memória específica foi solicitada, mas não pode ser atendida.</span><span class="sxs-lookup"><span data-stu-id="b0b38-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0b38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0b38-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="b0b38-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b0b38-105">Members</span></span>  
  
|<span data-ttu-id="b0b38-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b0b38-106">Member</span></span>|<span data-ttu-id="b0b38-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0b38-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="b0b38-108">Indica que a alocação é fundamental para a execução de código gerenciado no domínio que solicitou a alocação.</span><span class="sxs-lookup"><span data-stu-id="b0b38-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="b0b38-109">Se não é possível alocar a memória, o CLR não pode garantir que o domínio é utilizável.</span><span class="sxs-lookup"><span data-stu-id="b0b38-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="b0b38-110">O host decide qual ação a ser tomada quando a alocação não pode ser atendida.</span><span class="sxs-lookup"><span data-stu-id="b0b38-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="b0b38-111">Ele pode instruir o CLR para anular o `AppDomain` automaticamente, ou permitir que ele seja executado chamando métodos na [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b0b38-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="b0b38-112">Indica que a alocação é fundamental para a execução de código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="b0b38-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="b0b38-113">Esse valor é usado durante a inicialização e ao executar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="b0b38-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="b0b38-114">Se não é possível alocar a memória, o CLR não pode operar no processo.</span><span class="sxs-lookup"><span data-stu-id="b0b38-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="b0b38-115">Se a alocação falhar, o CLR está desativado.</span><span class="sxs-lookup"><span data-stu-id="b0b38-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="b0b38-116">Todas as chamadas subsequentes para o CLR falharem com HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b0b38-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="b0b38-117">Indica que a alocação é fundamental para a execução da tarefa que solicitou a alocação.</span><span class="sxs-lookup"><span data-stu-id="b0b38-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="b0b38-118">Se não é possível alocar a memória, o CLR não pode garantir que a tarefa pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="b0b38-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="b0b38-119">No caso de falha, o CLR gera um <xref:System.Threading.ThreadAbortException> no thread de operação física do sistema.</span><span class="sxs-lookup"><span data-stu-id="b0b38-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0b38-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0b38-120">Remarks</span></span>  
 <span data-ttu-id="b0b38-121">Os métodos de alocação de memória definidos a [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) e [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces usam um parâmetro deste tipo.</span><span class="sxs-lookup"><span data-stu-id="b0b38-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="b0b38-122">Dependendo da gravidade de falha, um host pode decidir se falhar a solicitação de alocação imediatamente ou aguardar até que ele pode ser atendido.</span><span class="sxs-lookup"><span data-stu-id="b0b38-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0b38-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0b38-123">Requirements</span></span>  
 <span data-ttu-id="b0b38-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0b38-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0b38-125">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b0b38-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0b38-126">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0b38-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0b38-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0b38-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b38-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0b38-128">See Also</span></span>  
 [<span data-ttu-id="b0b38-129">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="b0b38-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="b0b38-130">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b0b38-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
