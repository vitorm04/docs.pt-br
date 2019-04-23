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
ms.openlocfilehash: 60997717baf70e10366e7f0ba6a06daa1f35f8cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121661"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="75240-102">Método ICLRTask2::EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="75240-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="75240-103">Permite que novos ou thread anulação solicitações pendentes para resultar em thread anula no thread atual.</span><span class="sxs-lookup"><span data-stu-id="75240-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75240-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75240-104">Syntax</span></span>  
  
```  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="75240-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="75240-105">Return Value</span></span>  
 <span data-ttu-id="75240-106">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="75240-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="75240-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75240-107">HRESULT</span></span>|<span data-ttu-id="75240-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="75240-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75240-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="75240-109">S_OK</span></span>|<span data-ttu-id="75240-110">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="75240-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="75240-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="75240-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="75240-112">O método foi chamado em um thread que não é o thread atual.</span><span class="sxs-lookup"><span data-stu-id="75240-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75240-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="75240-113">Remarks</span></span>  
 <span data-ttu-id="75240-114">Chamando esse contador do método diminui o atraso--anulação de thread para o thread atual por um.</span><span class="sxs-lookup"><span data-stu-id="75240-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="75240-115">Chamadas para [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) e `EndPreventAsyncAbort` podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="75240-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="75240-116">Desde que o contador for maior que zero, as anulações de thread para o thread atual são atrasadas.</span><span class="sxs-lookup"><span data-stu-id="75240-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="75240-117">A funcionalidade que é exposta por esse recurso é usada internamente pela máquina virtual (VM).</span><span class="sxs-lookup"><span data-stu-id="75240-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="75240-118">Uso indevido desses métodos pode causar comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="75240-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="75240-119">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` foi possível definir o contador como zero quando a VM é incrementado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="75240-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="75240-120">Da mesma forma, o contador interno não é verificado para estouro.</span><span class="sxs-lookup"><span data-stu-id="75240-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="75240-121">Se ele exceder seu limite de integral porque ele é incrementado pelo host e a VM, o comportamento resultante é especificado.</span><span class="sxs-lookup"><span data-stu-id="75240-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75240-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75240-122">Requirements</span></span>  
 <span data-ttu-id="75240-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75240-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75240-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75240-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75240-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="75240-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75240-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75240-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75240-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75240-127">See also</span></span>

- [<span data-ttu-id="75240-128">Método BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="75240-128">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="75240-129">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="75240-129">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="75240-130">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="75240-130">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="75240-131">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="75240-131">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="75240-132">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="75240-132">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="75240-133">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="75240-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
