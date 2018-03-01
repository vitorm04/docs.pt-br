---
title: "Enumeração EClrOperation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 343ff04dba1a02660734beb726f9b895370a10af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="7818b-102">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="7818b-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="7818b-103">Descreve o conjunto de operações para o qual um host pode aplicar as ações de política.</span><span class="sxs-lookup"><span data-stu-id="7818b-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7818b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7818b-104">Syntax</span></span>  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="7818b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7818b-105">Members</span></span>  
  
|<span data-ttu-id="7818b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7818b-106">Member</span></span>|<span data-ttu-id="7818b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7818b-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="7818b-108">O host pode especificar ações de política a ser tomada quando um <xref:System.AppDomain> é descarregado de maneira não normal (educada).</span><span class="sxs-lookup"><span data-stu-id="7818b-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="7818b-109">O host pode especificar ações de política a ser tomada quando um <xref:System.AppDomain> é descarregado.</span><span class="sxs-lookup"><span data-stu-id="7818b-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="7818b-110">O host pode especificar ações de política a ser tomada quando executar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="7818b-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="7818b-111">O host pode especificar ações de política a ser tomada quando o processo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="7818b-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="7818b-112">O host pode especificar ações de política a ser tomada quando um thread é anulado.</span><span class="sxs-lookup"><span data-stu-id="7818b-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="7818b-113">O host pode especificar ações de política a ser tomada quando uma anulação de thread educado ocorre em uma região crítica de código.</span><span class="sxs-lookup"><span data-stu-id="7818b-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="7818b-114">O host pode especificar ações de política para ser executada quando uma anulação de thread educado ocorre em uma região não críticos do código.</span><span class="sxs-lookup"><span data-stu-id="7818b-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7818b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="7818b-115">Remarks</span></span>  
 <span data-ttu-id="7818b-116">A infra-estrutura de confiabilidade do common language runtime (CLR) faz distinção entre recursos e anulações de falhas de alocação que ocorrem em regiões críticas de código e os que ocorrem em regiões não críticos do código.</span><span class="sxs-lookup"><span data-stu-id="7818b-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="7818b-117">Essa distinção foi projetada para permitir que os hosts definir políticas diferentes dependendo de onde ocorrer uma falha no código.</span><span class="sxs-lookup"><span data-stu-id="7818b-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="7818b-118">Um *região crítica de código* qualquer espaço em que o CLR não pode garantir que anular uma tarefa ou uma falha ao concluir uma solicitação de recursos afeta apenas a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="7818b-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="7818b-119">Por exemplo, se uma tarefa está mantendo um bloqueio e recebe um HRESULT que indica falha ao fazer uma solicitação de alocação de memória, é suficiente apenas para anular essa tarefa para garantir a estabilidade do <xref:System.AppDomain>, pois o <xref:System.AppDomain> pode conter outros tarefas em espera para o mesmo bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7818b-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="7818b-120">Para abandonar atual tarefa pode fazer com que as outras tarefas parar de responder (ou desligar) indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="7818b-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="7818b-121">Nesse caso, o host precisa da capacidade de descarregar todo o <xref:System.AppDomain> em vez de possível instabilidade de risco.</span><span class="sxs-lookup"><span data-stu-id="7818b-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="7818b-122">Um *região não críticos do código*, por outro lado, é uma região em que o CLR pode garantir que uma operação de anulação ou uma falha de afetará apenas a tarefa na qual o erro ocorrer.</span><span class="sxs-lookup"><span data-stu-id="7818b-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="7818b-123">O CLR também faz distinção entre normais e não normal anulações (educadas).</span><span class="sxs-lookup"><span data-stu-id="7818b-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="7818b-124">Em geral, uma anulação normal ou normal faz todos os esforços para executar rotinas de manipulação de exceção e finalizadores antes de cancelar uma tarefa, enquanto uma anulação educada não garante tais.</span><span class="sxs-lookup"><span data-stu-id="7818b-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7818b-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7818b-125">Requirements</span></span>  
 <span data-ttu-id="7818b-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7818b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7818b-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7818b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7818b-128">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7818b-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7818b-129">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7818b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7818b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7818b-130">See Also</span></span>  
 [<span data-ttu-id="7818b-131">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="7818b-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="7818b-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="7818b-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="7818b-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="7818b-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="7818b-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="7818b-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="7818b-135">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="7818b-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
