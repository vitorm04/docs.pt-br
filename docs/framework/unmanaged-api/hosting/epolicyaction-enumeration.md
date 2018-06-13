---
title: Enumeração EPolicyAction
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14908ae641c8539659e6014deb2c5f35a6d1cfbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433624"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="222a1-102">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="222a1-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="222a1-103">Descreve as ações de política, o host pode ser definido para operações descritas por [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) e falhas descritas por [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="222a1-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="222a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="222a1-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="222a1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="222a1-105">Members</span></span>  
  
|<span data-ttu-id="222a1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="222a1-106">Member</span></span>|<span data-ttu-id="222a1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="222a1-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="222a1-108">Especifica que o common language runtime (CLR) deve anular o thread normalmente.</span><span class="sxs-lookup"><span data-stu-id="222a1-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="222a1-109">Uma anulação normal inclui tentativas para executar todos os `finally` bloqueia qualquer `catch` blocos relacionados a anulações de thread e finalizadores.</span><span class="sxs-lookup"><span data-stu-id="222a1-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="222a1-110">Especifica que o CLR deve entrar em um estado desabilitado.</span><span class="sxs-lookup"><span data-stu-id="222a1-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="222a1-111">Nenhum outro código gerenciado pode ser executado no processo de afetados e threads são impedidos de inserir o CLR.</span><span class="sxs-lookup"><span data-stu-id="222a1-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="222a1-112">Especifica que o CLR deve tentar uma saída normal do processo, incluindo a execução de finalizadores e executar operações de registro em log e limpeza.</span><span class="sxs-lookup"><span data-stu-id="222a1-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="222a1-113">Especifica que o CLR deve sair do processo imediatamente, sem executar finalizadores ou executar limpeza e operações de log.</span><span class="sxs-lookup"><span data-stu-id="222a1-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="222a1-114">Nowever, a notificação é enviada para o depurador.</span><span class="sxs-lookup"><span data-stu-id="222a1-114">Nowever, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="222a1-115">Especifica que nenhuma ação deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="222a1-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="222a1-116">Especifica que o CLR deve realizar uma anulação de thread educado.</span><span class="sxs-lookup"><span data-stu-id="222a1-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="222a1-117">Somente os `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="222a1-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="222a1-118">Especifica que o CLR deve sair do processo sem executar finalizadores ou operações de log.</span><span class="sxs-lookup"><span data-stu-id="222a1-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="222a1-119">Especifica que o CLR deve realizar um descarregamento educado do <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="222a1-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="222a1-120">Finalizadores somente marcado com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="222a1-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="222a1-121">Da mesma forma, todos os threads com essa <xref:System.AppDomain> em sua pilha receber um `ThreadAbortException`, mas somente aqueles `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="222a1-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="222a1-122">Especifica que uma exceção apropriada para a condição, como falta de memória, estouro de buffer e assim por diante, deverá ser lançada.</span><span class="sxs-lookup"><span data-stu-id="222a1-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="222a1-123">Especifica que o <xref:System.AppDomain> deve ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="222a1-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="222a1-124">O CLR tentará executar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="222a1-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="222a1-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="222a1-125">Remarks</span></span>  
 <span data-ttu-id="222a1-126">O host define as ações de política chamando métodos do [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="222a1-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="222a1-127">Para obter informações sobre anulações educadas e normais, consulte o [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="222a1-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="222a1-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="222a1-128">Requirements</span></span>  
 <span data-ttu-id="222a1-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="222a1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="222a1-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="222a1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="222a1-131">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="222a1-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="222a1-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="222a1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222a1-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="222a1-133">See Also</span></span>  
 [<span data-ttu-id="222a1-134">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="222a1-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="222a1-135">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="222a1-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="222a1-136">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="222a1-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="222a1-137">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="222a1-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
