---
title: "Método ICLRTask2::EndPreventAsyncAbort"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b18f6b8f6768c0a2980489cf8b84e16a9dd31350
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="cae16-102">Método ICLRTask2::EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="cae16-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="cae16-103">Permite que novos ou pendente solicitações de anulação de thread resultará em thread anulada no thread atual.</span><span class="sxs-lookup"><span data-stu-id="cae16-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cae16-104">Syntax</span></span>  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cae16-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cae16-105">Return Value</span></span>  
 <span data-ttu-id="cae16-106">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="cae16-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cae16-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cae16-107">HRESULT</span></span>|<span data-ttu-id="cae16-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="cae16-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cae16-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="cae16-109">S_OK</span></span>|<span data-ttu-id="cae16-110">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="cae16-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="cae16-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="cae16-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="cae16-112">O método foi chamado em um thread que não seja o thread atual.</span><span class="sxs-lookup"><span data-stu-id="cae16-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cae16-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="cae16-113">Remarks</span></span>  
 <span data-ttu-id="cae16-114">Chamar esse contador diminui a anulação de atraso-thread de método para o thread atual por um.</span><span class="sxs-lookup"><span data-stu-id="cae16-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="cae16-115">Chamadas para [Iclrtask2](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) e `EndPreventAsyncAbort` podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="cae16-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="cae16-116">Como o contador for maior que zero, anulações de thread para o thread atual estão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="cae16-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="cae16-117">A funcionalidade que é exposta por este recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="cae16-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="cae16-118">Uso indevido dos métodos a seguir pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="cae16-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="cae16-119">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador para zero quando a VM foi incrementada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cae16-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="cae16-120">Da mesma forma, o contador interno não é verificado de estouro.</span><span class="sxs-lookup"><span data-stu-id="cae16-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="cae16-121">Se ele exceder o limite de integral porque ele é incrementado pelo host e a máquina virtual, o comportamento resultante é não especificado.</span><span class="sxs-lookup"><span data-stu-id="cae16-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cae16-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cae16-122">Requirements</span></span>  
 <span data-ttu-id="cae16-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cae16-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cae16-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cae16-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cae16-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cae16-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cae16-126">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cae16-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae16-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cae16-127">See Also</span></span>  
 [<span data-ttu-id="cae16-128">Método BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="cae16-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)  
 [<span data-ttu-id="cae16-129">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="cae16-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="cae16-130">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="cae16-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cae16-131">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="cae16-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="cae16-132">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="cae16-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="cae16-133">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="cae16-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
