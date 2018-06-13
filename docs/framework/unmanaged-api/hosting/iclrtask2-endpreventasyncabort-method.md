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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cacc96d66d5d4eb46c08c93d9c2793282627539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438227"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="ec562-102">Método ICLRTask2::EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="ec562-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="ec562-103">Permite que novos ou pendente solicitações de anulação de thread resultará em thread anulada no thread atual.</span><span class="sxs-lookup"><span data-stu-id="ec562-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec562-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec562-104">Syntax</span></span>  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ec562-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ec562-105">Return Value</span></span>  
 <span data-ttu-id="ec562-106">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="ec562-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ec562-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec562-107">HRESULT</span></span>|<span data-ttu-id="ec562-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec562-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec562-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec562-109">S_OK</span></span>|<span data-ttu-id="ec562-110">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="ec562-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="ec562-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="ec562-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="ec562-112">O método foi chamado em um thread que não seja o thread atual.</span><span class="sxs-lookup"><span data-stu-id="ec562-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec562-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec562-113">Remarks</span></span>  
 <span data-ttu-id="ec562-114">Chamar esse contador diminui a anulação de atraso-thread de método para o thread atual por um.</span><span class="sxs-lookup"><span data-stu-id="ec562-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="ec562-115">Chamadas para [Iclrtask2](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) e `EndPreventAsyncAbort` podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="ec562-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="ec562-116">Como o contador for maior que zero, anulações de thread para o thread atual estão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="ec562-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="ec562-117">A funcionalidade que é exposta por este recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="ec562-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="ec562-118">Uso indevido dos métodos a seguir pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="ec562-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="ec562-119">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador para zero quando a VM foi incrementada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ec562-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="ec562-120">Da mesma forma, o contador interno não é verificado de estouro.</span><span class="sxs-lookup"><span data-stu-id="ec562-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="ec562-121">Se ele exceder o limite de integral porque ele é incrementado pelo host e a máquina virtual, o comportamento resultante é não especificado.</span><span class="sxs-lookup"><span data-stu-id="ec562-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec562-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec562-122">Requirements</span></span>  
 <span data-ttu-id="ec562-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec562-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec562-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec562-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec562-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ec562-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec562-126">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec562-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec562-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec562-127">See Also</span></span>  
 [<span data-ttu-id="ec562-128">Método BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="ec562-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)  
 [<span data-ttu-id="ec562-129">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="ec562-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="ec562-130">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="ec562-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ec562-131">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="ec562-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ec562-132">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="ec562-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="ec562-133">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ec562-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
