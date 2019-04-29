---
title: Método ICLRTask2::BeginPreventAsyncAbort
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a43fef7f6dfa6dbe0bb9f1c4caec2c9c224b93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763425"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="96e3a-102">Método ICLRTask2::BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="96e3a-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="96e3a-103">Novo thread de atrasos de anulação de solicitações de resultando em anulações de thread no thread atual.</span><span class="sxs-lookup"><span data-stu-id="96e3a-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96e3a-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="96e3a-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="96e3a-105">Return Value</span></span>  
 <span data-ttu-id="96e3a-106">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="96e3a-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="96e3a-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96e3a-107">HRESULT</span></span>|<span data-ttu-id="96e3a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="96e3a-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96e3a-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="96e3a-109">S_OK</span></span>|<span data-ttu-id="96e3a-110">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="96e3a-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="96e3a-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="96e3a-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="96e3a-112">O método foi chamado em um thread que não é o thread atual.</span><span class="sxs-lookup"><span data-stu-id="96e3a-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96e3a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="96e3a-113">Remarks</span></span>  
 <span data-ttu-id="96e3a-114">Chamar esse método incrementa o contador de anulação de thread de atraso para o thread atual em um.</span><span class="sxs-lookup"><span data-stu-id="96e3a-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="96e3a-115">Chamadas para `BeginPreventAsyncAbort` e [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="96e3a-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="96e3a-116">Desde que o contador for maior que zero, as anulações de thread para o thread atual são atrasadas.</span><span class="sxs-lookup"><span data-stu-id="96e3a-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="96e3a-117">Se essa chamada não está emparelhada com uma chamada para o `EndPreventAsyncAbort` método, é possível atingir um estado no qual thread anulações não podem ser entregues ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="96e3a-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="96e3a-118">O atraso é respeitado para um thread que anula a mesmo.</span><span class="sxs-lookup"><span data-stu-id="96e3a-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="96e3a-119">A funcionalidade que é exposta por esse recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="96e3a-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="96e3a-120">Uso indevido desses métodos pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="96e3a-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="96e3a-121">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador como zero quando a VM é incrementado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="96e3a-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="96e3a-122">Da mesma forma, o contador interno não é verificado para estouro.</span><span class="sxs-lookup"><span data-stu-id="96e3a-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="96e3a-123">Se ele exceder seu limite de integral porque ele é incrementado pelo host e a VM, o comportamento resultante é especificado.</span><span class="sxs-lookup"><span data-stu-id="96e3a-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e3a-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96e3a-124">Requirements</span></span>  
 <span data-ttu-id="96e3a-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96e3a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e3a-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96e3a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96e3a-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="96e3a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96e3a-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e3a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e3a-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96e3a-129">See also</span></span>

- [<span data-ttu-id="96e3a-130">Método EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="96e3a-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="96e3a-131">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="96e3a-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="96e3a-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="96e3a-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="96e3a-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="96e3a-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="96e3a-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="96e3a-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="96e3a-135">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="96e3a-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
