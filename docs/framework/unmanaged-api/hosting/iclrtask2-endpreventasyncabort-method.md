---
title: Método ICLRTask2::EndPreventAsyncAbort
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 8ae66e0bf96138e5bc2f33e4c14ad86e7dabc6b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124547"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="1be86-102">Método ICLRTask2::EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="1be86-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="1be86-103">Permite solicitações de anulação de thread novas ou pendentes para resultar em anulações de thread no thread atual.</span><span class="sxs-lookup"><span data-stu-id="1be86-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be86-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1be86-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1be86-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1be86-105">Return Value</span></span>  
 <span data-ttu-id="1be86-106">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="1be86-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1be86-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1be86-107">HRESULT</span></span>|<span data-ttu-id="1be86-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="1be86-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1be86-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="1be86-109">S_OK</span></span>|<span data-ttu-id="1be86-110">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="1be86-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="1be86-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="1be86-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="1be86-112">O método foi chamado em um thread que não é o thread atual.</span><span class="sxs-lookup"><span data-stu-id="1be86-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1be86-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1be86-113">Remarks</span></span>  
 <span data-ttu-id="1be86-114">Chamar esse método diminui o contador atraso-thread-anulação do thread atual em um.</span><span class="sxs-lookup"><span data-stu-id="1be86-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="1be86-115">As chamadas para [ICLRTask2:: BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) e `EndPreventAsyncAbort` podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="1be86-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="1be86-116">Desde que o contador seja maior que zero, as anulações de thread para o thread atual serão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="1be86-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="1be86-117">A funcionalidade exposta por esse recurso é usada internamente pela VM (máquina virtual).</span><span class="sxs-lookup"><span data-stu-id="1be86-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="1be86-118">O uso indevido desses métodos pode causar um comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="1be86-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="1be86-119">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` pode definir o contador como zero quando a VM o incrementaa anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1be86-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="1be86-120">Da mesma forma, o contador interno não é verificado quanto ao estouro.</span><span class="sxs-lookup"><span data-stu-id="1be86-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="1be86-121">Se ele exceder seu limite integral porque é incrementado pelo host e pela VM, o comportamento resultante não é especificado.</span><span class="sxs-lookup"><span data-stu-id="1be86-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1be86-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1be86-122">Requirements</span></span>  
 <span data-ttu-id="1be86-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1be86-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1be86-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1be86-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1be86-125">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1be86-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1be86-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1be86-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be86-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1be86-127">See also</span></span>

- [<span data-ttu-id="1be86-128">Método BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="1be86-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="1be86-129">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="1be86-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="1be86-130">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="1be86-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1be86-131">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="1be86-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1be86-132">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="1be86-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="1be86-133">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="1be86-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
