---
title: "Método ICLRTask2::BeginPreventAsyncAbort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2.BeginPreventAsyncAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33136dfbfa8bb3e0147bc1a1c1bb9e88ab2e4239
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="8c051-102">Método ICLRTask2::BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="8c051-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="8c051-103">Atrasos thread anular pedidos de novos resultando em anulações de thread no thread atual.</span><span class="sxs-lookup"><span data-stu-id="8c051-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c051-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c051-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8c051-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8c051-105">Return Value</span></span>  
 <span data-ttu-id="8c051-106">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="8c051-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8c051-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c051-107">HRESULT</span></span>|<span data-ttu-id="8c051-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c051-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c051-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c051-109">S_OK</span></span>|<span data-ttu-id="8c051-110">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="8c051-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="8c051-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="8c051-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="8c051-112">O método foi chamado em um thread que não seja o thread atual.</span><span class="sxs-lookup"><span data-stu-id="8c051-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c051-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c051-113">Remarks</span></span>  
 <span data-ttu-id="8c051-114">Chamar esse método incrementa o contador de anulação de thread de atraso para o thread atual por um.</span><span class="sxs-lookup"><span data-stu-id="8c051-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="8c051-115">Chamadas para `BeginPreventAsyncAbort` e [Iclrtask2](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="8c051-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="8c051-116">Como o contador for maior que zero, anulações de thread para o thread atual estão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="8c051-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="8c051-117">Se essa chamada não está emparelhada com uma chamada para o `EndPreventAsyncAbort` método, é possível atingir um estado no qual thread anulações não podem ser entregue ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="8c051-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="8c051-118">O atraso não é cumprido por um thread que anula a mesmo.</span><span class="sxs-lookup"><span data-stu-id="8c051-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="8c051-119">A funcionalidade que é exposta por este recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="8c051-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="8c051-120">Uso indevido dos métodos a seguir pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="8c051-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="8c051-121">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador para zero quando a VM foi incrementada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8c051-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="8c051-122">Da mesma forma, o contador interno não é verificado de estouro.</span><span class="sxs-lookup"><span data-stu-id="8c051-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="8c051-123">Se ele exceder o limite de integral porque ele é incrementado pelo host e a máquina virtual, o comportamento resultante é não especificado.</span><span class="sxs-lookup"><span data-stu-id="8c051-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c051-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c051-124">Requirements</span></span>  
 <span data-ttu-id="8c051-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c051-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c051-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c051-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c051-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8c051-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c051-128">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c051-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c051-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c051-129">See Also</span></span>  
 [<span data-ttu-id="8c051-130">Método EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="8c051-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)  
 [<span data-ttu-id="8c051-131">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="8c051-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="8c051-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="8c051-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="8c051-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="8c051-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="8c051-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="8c051-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="8c051-135">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="8c051-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
