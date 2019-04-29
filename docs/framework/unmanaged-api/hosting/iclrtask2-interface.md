---
title: Interface ICLRTask2
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518248651de6d8afdf25692c5f48da52b11eb0f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763393"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="169a1-102">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="169a1-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="169a1-103">Fornece a funcionalidade dos [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; Além disso, fornece métodos que permitem que as anulações de thread para ser atrasado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="169a1-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="169a1-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="169a1-104">Methods</span></span>  
  
|<span data-ttu-id="169a1-105">Método</span><span class="sxs-lookup"><span data-stu-id="169a1-105">Method</span></span>|<span data-ttu-id="169a1-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="169a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="169a1-107">Método BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="169a1-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="169a1-108">Novo thread de atrasos de anulação de solicitações no thread atual.</span><span class="sxs-lookup"><span data-stu-id="169a1-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="169a1-109">Método EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="169a1-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="169a1-110">Permite que novos ou thread anulação solicitações pendentes para resultar em thread anula no thread atual.</span><span class="sxs-lookup"><span data-stu-id="169a1-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="169a1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="169a1-111">Remarks</span></span>  
 <span data-ttu-id="169a1-112">O `ICLRTask2` interface herda o `ICLRTask` de interface e adiciona métodos que permitem que o host atrasar as anulações de thread, para proteger uma região de código que não deve falhar.</span><span class="sxs-lookup"><span data-stu-id="169a1-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="169a1-113">Chamando `BeginPreventAsyncAbort` incrementa o contador de anulação de thread de atraso para o thread atual e chamar `EndPreventAsyncAbort` diminui-lo.</span><span class="sxs-lookup"><span data-stu-id="169a1-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="169a1-114">Chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="169a1-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="169a1-115">Desde que o contador for maior que zero, as anulações de thread para o thread atual são atrasadas.</span><span class="sxs-lookup"><span data-stu-id="169a1-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="169a1-116">Se chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` não são emparelhadas, é possível atingir um estado no qual thread anulações não podem ser entregues ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="169a1-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="169a1-117">O atraso é respeitado para um thread que anula a mesmo.</span><span class="sxs-lookup"><span data-stu-id="169a1-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="169a1-118">A funcionalidade que é exposta por esse recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="169a1-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="169a1-119">Uso indevido desses métodos pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="169a1-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="169a1-120">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador como zero quando a VM é incrementado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="169a1-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="169a1-121">Da mesma forma, o contador interno não é verificado para estouro.</span><span class="sxs-lookup"><span data-stu-id="169a1-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="169a1-122">Se ele exceder seu limite de integral porque ele é incrementado pelo host e a VM, o comportamento resultante é especificado.</span><span class="sxs-lookup"><span data-stu-id="169a1-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="169a1-123">Para obter informações sobre membros herdada de `ICLRTask` e sobre outros usos dessa interface, consulte a [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="169a1-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="169a1-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="169a1-124">Requirements</span></span>  
 <span data-ttu-id="169a1-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="169a1-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="169a1-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="169a1-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="169a1-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="169a1-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="169a1-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="169a1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169a1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="169a1-129">See also</span></span>

- [<span data-ttu-id="169a1-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="169a1-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="169a1-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="169a1-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="169a1-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="169a1-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="169a1-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="169a1-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="169a1-134">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="169a1-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
