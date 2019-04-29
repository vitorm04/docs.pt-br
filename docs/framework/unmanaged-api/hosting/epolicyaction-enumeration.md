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
ms.openlocfilehash: 75bd7da67cbac958f0b34c8295454a719962c7ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628711"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="57b74-102">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="57b74-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="57b74-103">Descreve as ações de política, o host pode ser definido para operações descritas pelo [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) e as falhas descritas pelo [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="57b74-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57b74-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="57b74-105">Membros</span><span class="sxs-lookup"><span data-stu-id="57b74-105">Members</span></span>  
  
|<span data-ttu-id="57b74-106">Membro</span><span class="sxs-lookup"><span data-stu-id="57b74-106">Member</span></span>|<span data-ttu-id="57b74-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="57b74-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="57b74-108">Especifica que o common language runtime (CLR) deve anular o thread normalmente.</span><span class="sxs-lookup"><span data-stu-id="57b74-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="57b74-109">Uma anulação normal inclui tentativas de executar todos `finally` bloqueia qualquer `catch` blocos relacionados a anulações de thread e finalizadores.</span><span class="sxs-lookup"><span data-stu-id="57b74-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="57b74-110">Especifica que o CLR deve entrar em um estado desabilitado.</span><span class="sxs-lookup"><span data-stu-id="57b74-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="57b74-111">Nenhum outro código gerenciado pode ser executado no processo afetado e threads são bloqueados de inserir o CLR.</span><span class="sxs-lookup"><span data-stu-id="57b74-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="57b74-112">Especifica que o CLR deve tentar uma saída normal do processo, incluindo a execução de finalizadores e operações de registro em log e limpeza.</span><span class="sxs-lookup"><span data-stu-id="57b74-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="57b74-113">Especifica que o CLR deve sair do processo imediatamente, sem execução dos finalizadores ou executar a limpeza e operações de registro em log.</span><span class="sxs-lookup"><span data-stu-id="57b74-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="57b74-114">No entanto, a notificação é enviada para o depurador.</span><span class="sxs-lookup"><span data-stu-id="57b74-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="57b74-115">Especifica que nenhuma ação deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="57b74-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="57b74-116">Especifica que o CLR deve realizar uma anulação de thread rude.</span><span class="sxs-lookup"><span data-stu-id="57b74-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="57b74-117">Somente aqueles `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executadas.</span><span class="sxs-lookup"><span data-stu-id="57b74-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="57b74-118">Especifica que o CLR deve sair do processo sem execução dos finalizadores ou operações de registro em log.</span><span class="sxs-lookup"><span data-stu-id="57b74-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="57b74-119">Especifica que o CLR deve realizar um descarregamento de rude do <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="57b74-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="57b74-120">Os finalizadores apenas marcado com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executadas.</span><span class="sxs-lookup"><span data-stu-id="57b74-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="57b74-121">Da mesma forma, todos os threads com essa <xref:System.AppDomain> em sua pilha recebem um `ThreadAbortException`, mas somente os `catch` e `finally` blocos marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executadas.</span><span class="sxs-lookup"><span data-stu-id="57b74-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="57b74-122">Especifica que uma exceção apropriada para a condição, como falta de memória, o estouro de buffer e assim por diante, deve ser gerada.</span><span class="sxs-lookup"><span data-stu-id="57b74-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="57b74-123">Especifica que o <xref:System.AppDomain> deve ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="57b74-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="57b74-124">O CLR tenta executar os finalizadores.</span><span class="sxs-lookup"><span data-stu-id="57b74-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57b74-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="57b74-125">Remarks</span></span>  
 <span data-ttu-id="57b74-126">O host define as ações da política chamando métodos das [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="57b74-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="57b74-127">Para obter informações sobre as anulações rudes e normais, consulte o [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="57b74-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57b74-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57b74-128">Requirements</span></span>  
 <span data-ttu-id="57b74-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57b74-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57b74-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57b74-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57b74-131">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57b74-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57b74-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57b74-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b74-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57b74-133">See also</span></span>

- [<span data-ttu-id="57b74-134">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="57b74-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="57b74-135">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="57b74-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="57b74-136">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="57b74-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="57b74-137">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="57b74-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
