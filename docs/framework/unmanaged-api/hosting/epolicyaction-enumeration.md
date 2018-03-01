---
title: "Enumeração EPolicyAction"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5de55d46eead37962fad7d7c1c5bd1766e772fe8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="695dc-102">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="695dc-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="695dc-103">Descreve as ações de política, o host pode ser definido para operações descritas por [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) e falhas descritas por [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="695dc-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="695dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="695dc-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="695dc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="695dc-105">Members</span></span>  
  
|<span data-ttu-id="695dc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="695dc-106">Member</span></span>|<span data-ttu-id="695dc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="695dc-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="695dc-108">Especifica que o common language runtime (CLR) deve anular o thread normalmente.</span><span class="sxs-lookup"><span data-stu-id="695dc-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="695dc-109">Uma anulação normal inclui tentativas para executar todos os `finally` bloqueia qualquer `catch` blocos relacionados a anulações de thread e finalizadores.</span><span class="sxs-lookup"><span data-stu-id="695dc-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="695dc-110">Especifica que o CLR deve entrar em um estado desabilitado.</span><span class="sxs-lookup"><span data-stu-id="695dc-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="695dc-111">Nenhum outro código gerenciado pode ser executado no processo de afetados e threads são impedidos de inserir o CLR.</span><span class="sxs-lookup"><span data-stu-id="695dc-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="695dc-112">Especifica que o CLR deve tentar uma saída normal do processo, incluindo a execução de finalizadores e executar operações de registro em log e limpeza.</span><span class="sxs-lookup"><span data-stu-id="695dc-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="695dc-113">Especifica que o CLR deve sair do processo imediatamente, sem executar finalizadores ou executar limpeza e operações de log.</span><span class="sxs-lookup"><span data-stu-id="695dc-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="695dc-114">Nowever, a notificação é enviada para o depurador.</span><span class="sxs-lookup"><span data-stu-id="695dc-114">Nowever, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="695dc-115">Especifica que nenhuma ação deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="695dc-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="695dc-116">Especifica que o CLR deve realizar uma anulação de thread educado.</span><span class="sxs-lookup"><span data-stu-id="695dc-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="695dc-117">Somente os `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="695dc-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="695dc-118">Especifica que o CLR deve sair do processo sem executar finalizadores ou operações de log.</span><span class="sxs-lookup"><span data-stu-id="695dc-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="695dc-119">Especifica que o CLR deve realizar um descarregamento educado do <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="695dc-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="695dc-120">Finalizadores somente marcado com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="695dc-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="695dc-121">Da mesma forma, todos os threads com essa <xref:System.AppDomain> em sua pilha receber um `ThreadAbortException`, mas somente aqueles `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="695dc-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="695dc-122">Especifica que uma exceção apropriada para a condição, como falta de memória, estouro de buffer e assim por diante, deverá ser lançada.</span><span class="sxs-lookup"><span data-stu-id="695dc-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="695dc-123">Especifica que o <xref:System.AppDomain> deve ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="695dc-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="695dc-124">O CLR tentará executar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="695dc-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="695dc-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="695dc-125">Remarks</span></span>  
 <span data-ttu-id="695dc-126">O host define as ações de política chamando métodos do [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="695dc-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="695dc-127">Para obter informações sobre anulações educadas e normais, consulte o [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="695dc-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="695dc-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="695dc-128">Requirements</span></span>  
 <span data-ttu-id="695dc-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="695dc-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="695dc-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="695dc-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="695dc-131">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="695dc-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="695dc-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="695dc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="695dc-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="695dc-133">See Also</span></span>  
 [<span data-ttu-id="695dc-134">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="695dc-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="695dc-135">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="695dc-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="695dc-136">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="695dc-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="695dc-137">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="695dc-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
