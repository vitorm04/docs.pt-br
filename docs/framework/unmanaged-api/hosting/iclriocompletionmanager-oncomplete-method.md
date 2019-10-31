---
title: Método ICLRIoCompletionManager::OnComplete
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: b44a71137e39130bb0fe4c303fdff62c76d38cbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141015"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="14fe2-102">Método ICLRIoCompletionManager::OnComplete</span><span class="sxs-lookup"><span data-stu-id="14fe2-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="14fe2-103">Notifica o Common Language Runtime (CLR) do status de uma solicitação de e/s que foi feita usando uma chamada para o método [IHostIoCompletionManager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="14fe2-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14fe2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14fe2-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14fe2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14fe2-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="14fe2-106">no Um valor HRESULT que indica o status da operação de associação.</span><span class="sxs-lookup"><span data-stu-id="14fe2-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="14fe2-107">S_OK indica que a operação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="14fe2-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="14fe2-108">HOST_E_INTERRUPTED indica que a chamada foi encerrada antes da conclusão.</span><span class="sxs-lookup"><span data-stu-id="14fe2-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="14fe2-109">E_FAIL indica que ocorreu uma falha catastrófica desconhecida e irrecuperável.</span><span class="sxs-lookup"><span data-stu-id="14fe2-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="14fe2-110">no O número de bytes transferidos durante o processamento da solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="14fe2-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="14fe2-111">no Um ponteiro para a estrutura de `OVERLAPPED` que foi passada para a chamada para o método `IHostIoCompletionManager::Bind`.</span><span class="sxs-lookup"><span data-stu-id="14fe2-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14fe2-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="14fe2-112">Return Value</span></span>  
  
|<span data-ttu-id="14fe2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14fe2-113">HRESULT</span></span>|<span data-ttu-id="14fe2-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="14fe2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14fe2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="14fe2-115">S_OK</span></span>|<span data-ttu-id="14fe2-116">`OnComplete` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="14fe2-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="14fe2-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14fe2-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14fe2-118">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="14fe2-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="14fe2-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="14fe2-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="14fe2-120">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="14fe2-120">The call timed out.</span></span>|  
|<span data-ttu-id="14fe2-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="14fe2-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="14fe2-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="14fe2-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="14fe2-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="14fe2-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="14fe2-124">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="14fe2-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="14fe2-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14fe2-125">E_FAIL</span></span>|<span data-ttu-id="14fe2-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="14fe2-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="14fe2-127">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="14fe2-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="14fe2-128">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="14fe2-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14fe2-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="14fe2-129">Remarks</span></span>  
 <span data-ttu-id="14fe2-130">Se o host implementar uma abstração de conclusão de e/s, o CLR fará solicitações de e/s por meio do host usando métodos de [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="14fe2-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="14fe2-131">Em seguida, o host chama o método `OnComplete` para notificar o tempo de execução do resultado de tais solicitações.</span><span class="sxs-lookup"><span data-stu-id="14fe2-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14fe2-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14fe2-132">Requirements</span></span>  
 <span data-ttu-id="14fe2-133">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14fe2-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14fe2-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="14fe2-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14fe2-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="14fe2-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14fe2-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14fe2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14fe2-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14fe2-137">See also</span></span>

- [<span data-ttu-id="14fe2-138">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="14fe2-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="14fe2-139">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="14fe2-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="14fe2-140">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="14fe2-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
