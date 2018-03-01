---
title: Interface ICLRTask2
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
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8701cff3400e46660fac90486cf5648d29aa9972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="58dd1-102">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="58dd1-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="58dd1-103">Fornece toda a funcionalidade do [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; Além disso, fornece métodos que permitem cancelamentos do thread para ser atrasado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="58dd1-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58dd1-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="58dd1-104">Methods</span></span>  
  
|<span data-ttu-id="58dd1-105">Método</span><span class="sxs-lookup"><span data-stu-id="58dd1-105">Method</span></span>|<span data-ttu-id="58dd1-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="58dd1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58dd1-107">Método BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="58dd1-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="58dd1-108">Novo thread de atrasos de anulação de solicitações no thread atual.</span><span class="sxs-lookup"><span data-stu-id="58dd1-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="58dd1-109">Método EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="58dd1-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="58dd1-110">Permite que novos ou pendente solicitações de anulação de thread resultará em thread anulada no thread atual.</span><span class="sxs-lookup"><span data-stu-id="58dd1-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58dd1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="58dd1-111">Remarks</span></span>  
 <span data-ttu-id="58dd1-112">O `ICLRTask2` interface herda o `ICLRTask` interface e adiciona métodos que permitem que o host atrasar anulações de thread, para proteger uma região de código que não deve falhar.</span><span class="sxs-lookup"><span data-stu-id="58dd1-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="58dd1-113">Chamando `BeginPreventAsyncAbort` incrementa o contador de anulação de thread de atraso para o thread atual e chamar `EndPreventAsyncAbort` diminui-la.</span><span class="sxs-lookup"><span data-stu-id="58dd1-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="58dd1-114">Chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="58dd1-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="58dd1-115">Como o contador for maior que zero, anulações de thread para o thread atual estão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="58dd1-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="58dd1-116">Se chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` não são emparelhados, é possível atingir um estado no qual thread anulações não podem ser entregue ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="58dd1-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="58dd1-117">O atraso não é cumprido por um thread que anula a mesmo.</span><span class="sxs-lookup"><span data-stu-id="58dd1-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="58dd1-118">A funcionalidade que é exposta por este recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="58dd1-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="58dd1-119">Uso indevido dos métodos a seguir pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="58dd1-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="58dd1-120">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador para zero quando a VM foi incrementada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="58dd1-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="58dd1-121">Da mesma forma, o contador interno não é verificado de estouro.</span><span class="sxs-lookup"><span data-stu-id="58dd1-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="58dd1-122">Se ele exceder o limite de integral porque ele é incrementado pelo host e a máquina virtual, o comportamento resultante é não especificado.</span><span class="sxs-lookup"><span data-stu-id="58dd1-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="58dd1-123">Para obter informações sobre membros herdada do `ICLRTask` e sobre outros usos dessa interface, consulte o [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="58dd1-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58dd1-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58dd1-124">Requirements</span></span>  
 <span data-ttu-id="58dd1-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58dd1-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58dd1-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58dd1-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58dd1-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="58dd1-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58dd1-128">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58dd1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58dd1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58dd1-129">See Also</span></span>  
 [<span data-ttu-id="58dd1-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="58dd1-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="58dd1-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="58dd1-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="58dd1-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="58dd1-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="58dd1-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="58dd1-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="58dd1-134">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="58dd1-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
