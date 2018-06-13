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
ms.openlocfilehash: ed0d2ff3b64bab026087e13d54314eca86181d8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438802"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="877c6-102">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="877c6-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="877c6-103">Fornece toda a funcionalidade do [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; Além disso, fornece métodos que permitem cancelamentos do thread para ser atrasado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="877c6-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="877c6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="877c6-104">Methods</span></span>  
  
|<span data-ttu-id="877c6-105">Método</span><span class="sxs-lookup"><span data-stu-id="877c6-105">Method</span></span>|<span data-ttu-id="877c6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="877c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="877c6-107">Método BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="877c6-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="877c6-108">Novo thread de atrasos de anulação de solicitações no thread atual.</span><span class="sxs-lookup"><span data-stu-id="877c6-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="877c6-109">Método EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="877c6-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="877c6-110">Permite que novos ou pendente solicitações de anulação de thread resultará em thread anulada no thread atual.</span><span class="sxs-lookup"><span data-stu-id="877c6-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="877c6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="877c6-111">Remarks</span></span>  
 <span data-ttu-id="877c6-112">O `ICLRTask2` interface herda o `ICLRTask` interface e adiciona métodos que permitem que o host atrasar anulações de thread, para proteger uma região de código que não deve falhar.</span><span class="sxs-lookup"><span data-stu-id="877c6-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="877c6-113">Chamando `BeginPreventAsyncAbort` incrementa o contador de anulação de thread de atraso para o thread atual e chamar `EndPreventAsyncAbort` diminui-la.</span><span class="sxs-lookup"><span data-stu-id="877c6-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="877c6-114">Chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="877c6-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="877c6-115">Como o contador for maior que zero, anulações de thread para o thread atual estão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="877c6-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="877c6-116">Se chamadas para `BeginPreventAsyncAbort` e `EndPreventAsyncAbort` não são emparelhados, é possível atingir um estado no qual thread anulações não podem ser entregue ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="877c6-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="877c6-117">O atraso não é cumprido por um thread que anula a mesmo.</span><span class="sxs-lookup"><span data-stu-id="877c6-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="877c6-118">A funcionalidade que é exposta por este recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="877c6-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="877c6-119">Uso indevido dos métodos a seguir pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="877c6-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="877c6-120">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador para zero quando a VM foi incrementada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="877c6-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="877c6-121">Da mesma forma, o contador interno não é verificado de estouro.</span><span class="sxs-lookup"><span data-stu-id="877c6-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="877c6-122">Se ele exceder o limite de integral porque ele é incrementado pelo host e a máquina virtual, o comportamento resultante é não especificado.</span><span class="sxs-lookup"><span data-stu-id="877c6-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="877c6-123">Para obter informações sobre membros herdada do `ICLRTask` e sobre outros usos dessa interface, consulte o [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="877c6-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="877c6-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="877c6-124">Requirements</span></span>  
 <span data-ttu-id="877c6-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="877c6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="877c6-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="877c6-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="877c6-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="877c6-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="877c6-128">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="877c6-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877c6-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="877c6-129">See Also</span></span>  
 [<span data-ttu-id="877c6-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="877c6-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="877c6-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="877c6-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="877c6-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="877c6-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="877c6-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="877c6-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="877c6-134">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="877c6-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
