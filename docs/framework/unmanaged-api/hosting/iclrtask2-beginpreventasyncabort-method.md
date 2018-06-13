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
ms.openlocfilehash: 5e1b5c0f5636748b96cc7d9667155581f1595a4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438399"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="0316f-102">Método ICLRTask2::BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="0316f-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="0316f-103">Atrasos thread anular pedidos de novos resultando em anulações de thread no thread atual.</span><span class="sxs-lookup"><span data-stu-id="0316f-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0316f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0316f-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0316f-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0316f-105">Return Value</span></span>  
 <span data-ttu-id="0316f-106">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="0316f-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0316f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0316f-107">HRESULT</span></span>|<span data-ttu-id="0316f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="0316f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0316f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="0316f-109">S_OK</span></span>|<span data-ttu-id="0316f-110">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="0316f-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="0316f-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="0316f-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="0316f-112">O método foi chamado em um thread que não seja o thread atual.</span><span class="sxs-lookup"><span data-stu-id="0316f-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0316f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0316f-113">Remarks</span></span>  
 <span data-ttu-id="0316f-114">Chamar esse método incrementa o contador de anulação de thread de atraso para o thread atual por um.</span><span class="sxs-lookup"><span data-stu-id="0316f-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="0316f-115">Chamadas para `BeginPreventAsyncAbort` e [Iclrtask2](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="0316f-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="0316f-116">Como o contador for maior que zero, anulações de thread para o thread atual estão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="0316f-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="0316f-117">Se essa chamada não está emparelhada com uma chamada para o `EndPreventAsyncAbort` método, é possível atingir um estado no qual thread anulações não podem ser entregue ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="0316f-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="0316f-118">O atraso não é cumprido por um thread que anula a mesmo.</span><span class="sxs-lookup"><span data-stu-id="0316f-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="0316f-119">A funcionalidade que é exposta por este recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="0316f-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="0316f-120">Uso indevido dos métodos a seguir pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="0316f-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="0316f-121">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador para zero quando a VM foi incrementada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0316f-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="0316f-122">Da mesma forma, o contador interno não é verificado de estouro.</span><span class="sxs-lookup"><span data-stu-id="0316f-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="0316f-123">Se ele exceder o limite de integral porque ele é incrementado pelo host e a máquina virtual, o comportamento resultante é não especificado.</span><span class="sxs-lookup"><span data-stu-id="0316f-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0316f-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0316f-124">Requirements</span></span>  
 <span data-ttu-id="0316f-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0316f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0316f-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0316f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0316f-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0316f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0316f-128">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0316f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0316f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0316f-129">See Also</span></span>  
 [<span data-ttu-id="0316f-130">Método EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="0316f-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)  
 [<span data-ttu-id="0316f-131">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="0316f-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="0316f-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="0316f-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0316f-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="0316f-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0316f-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="0316f-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="0316f-135">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="0316f-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
