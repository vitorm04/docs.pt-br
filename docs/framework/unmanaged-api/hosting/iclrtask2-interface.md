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
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124519"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="b0b4a-102">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="b0b4a-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="b0b4a-103">Fornece toda a funcionalidade da interface [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ; Além disso, o fornece métodos que permitem que as anulações de thread sejam atrasadas no thread atual.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0b4a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b0b4a-104">Methods</span></span>  
  
|<span data-ttu-id="b0b4a-105">Método</span><span class="sxs-lookup"><span data-stu-id="b0b4a-105">Method</span></span>|<span data-ttu-id="b0b4a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0b4a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0b4a-107">Método BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="b0b4a-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="b0b4a-108">Atrasa novas solicitações de anulação de thread no thread atual.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="b0b4a-109">Método EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="b0b4a-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="b0b4a-110">Permite solicitações de anulação de thread novas ou pendentes para resultar em anulações de thread no thread atual.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0b4a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0b4a-111">Remarks</span></span>  
 <span data-ttu-id="b0b4a-112">A interface `ICLRTask2` herda a interface `ICLRTask` e adiciona métodos que permitem ao host atrasar anulações de thread, proteger uma região de código que não deve falhar.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="b0b4a-113">Chamar `BeginPreventAsyncAbort` incrementa o contador atraso-thread-anulação para o thread atual e chamar `EndPreventAsyncAbort` decrementa-lo.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="b0b4a-114">As chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="b0b4a-115">Desde que o contador seja maior que zero, as anulações de thread para o thread atual serão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="b0b4a-116">Se as chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` não forem emparelhadas, é possível alcançar um estado no qual as anulações de thread não podem ser entregues ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="b0b4a-117">O atraso não é respeitado para um thread que se anula.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="b0b4a-118">A funcionalidade exposta por esse recurso é usada internamente pela VM (máquina virtual).</span><span class="sxs-lookup"><span data-stu-id="b0b4a-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="b0b4a-119">O uso indevido desses métodos pode causar um comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="b0b4a-120">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` pode definir o contador como zero quando a VM o incrementaa anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="b0b4a-121">Da mesma forma, o contador interno não é verificado quanto ao estouro.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="b0b4a-122">Se ele exceder seu limite integral porque é incrementado pelo host e pela VM, o comportamento resultante não é especificado.</span><span class="sxs-lookup"><span data-stu-id="b0b4a-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="b0b4a-123">Para obter informações sobre membros herdados de `ICLRTask` e sobre outros usos dessa interface, consulte a interface [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b0b4a-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0b4a-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0b4a-124">Requirements</span></span>  
 <span data-ttu-id="b0b4a-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0b4a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0b4a-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b0b4a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0b4a-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b0b4a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0b4a-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0b4a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b4a-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0b4a-129">See also</span></span>

- [<span data-ttu-id="b0b4a-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="b0b4a-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b0b4a-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b0b4a-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b0b4a-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="b0b4a-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b0b4a-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="b0b4a-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="b0b4a-134">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b0b4a-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
