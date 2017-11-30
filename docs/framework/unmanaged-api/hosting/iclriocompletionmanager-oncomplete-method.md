---
title: "Método ICLRIoCompletionManager::OnComplete"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager.OnComplete
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd38679d1b8d099e5eb6330e03e2333b03780dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="64a0b-102">Método ICLRIoCompletionManager::OnComplete</span><span class="sxs-lookup"><span data-stu-id="64a0b-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="64a0b-103">Notifica o common language runtime (CLR) do status de uma solicitação de e/s foi feita usando uma chamada para o [Ihostiocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="64a0b-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a0b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64a0b-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64a0b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64a0b-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="64a0b-106">[in] Um valor HRESULT que indica o status da operação de ligação.</span><span class="sxs-lookup"><span data-stu-id="64a0b-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
-   <span data-ttu-id="64a0b-107">S_OK indica que a operação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="64a0b-107">S_OK indicates that the operation completed successfully.</span></span>  
  
-   <span data-ttu-id="64a0b-108">HOST_E_INTERRUPTED indica que a chamada encerrado antes da conclusão.</span><span class="sxs-lookup"><span data-stu-id="64a0b-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
-   <span data-ttu-id="64a0b-109">E_FAIL indica que ocorreu uma falha catastrófica, irrecuperável desconhecida.</span><span class="sxs-lookup"><span data-stu-id="64a0b-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="64a0b-110">[in] O número de bytes transferidos durante o processamento da solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="64a0b-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="64a0b-111">[in] Um ponteiro para o `OVERLAPPED` estrutura que foi passada para a chamada para o `IHostIoCompletionManager::Bind` método.</span><span class="sxs-lookup"><span data-stu-id="64a0b-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64a0b-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="64a0b-112">Return Value</span></span>  
  
|<span data-ttu-id="64a0b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64a0b-113">HRESULT</span></span>|<span data-ttu-id="64a0b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="64a0b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64a0b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="64a0b-115">S_OK</span></span>|<span data-ttu-id="64a0b-116">`OnComplete`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="64a0b-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="64a0b-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="64a0b-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="64a0b-118">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="64a0b-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="64a0b-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="64a0b-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="64a0b-120">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="64a0b-120">The call timed out.</span></span>|  
|<span data-ttu-id="64a0b-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="64a0b-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="64a0b-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="64a0b-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="64a0b-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="64a0b-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="64a0b-124">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="64a0b-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="64a0b-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="64a0b-125">E_FAIL</span></span>|<span data-ttu-id="64a0b-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="64a0b-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="64a0b-127">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="64a0b-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="64a0b-128">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="64a0b-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64a0b-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="64a0b-129">Remarks</span></span>  
 <span data-ttu-id="64a0b-130">Se o host implementa uma abstração de conclusão de e/s, o CLR faz solicitações de e/s através do host usando métodos de [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="64a0b-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="64a0b-131">O host, em seguida, chama o `OnComplete` método para notificar o tempo de execução do resultado dessas solicitações.</span><span class="sxs-lookup"><span data-stu-id="64a0b-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64a0b-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64a0b-132">Requirements</span></span>  
 <span data-ttu-id="64a0b-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64a0b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64a0b-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="64a0b-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64a0b-135">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="64a0b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64a0b-136">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64a0b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a0b-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64a0b-137">See Also</span></span>  
 [<span data-ttu-id="64a0b-138">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="64a0b-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="64a0b-139">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="64a0b-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="64a0b-140">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="64a0b-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
