---
title: "Método IHostIoCompletionManager::GetMaxThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d02b0ba4802b72932ea6d23c66153c265a3d6498
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="36d77-102">Método IHostIoCompletionManager::GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="36d77-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="36d77-103">Obtém o número máximo de threads que o host pode alocar solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="36d77-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36d77-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36d77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36d77-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="36d77-106">[out] Um ponteiro para o número máximo de threads no pool de threads que o host pode alocar solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="36d77-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36d77-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="36d77-107">Return Value</span></span>  
  
|<span data-ttu-id="36d77-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36d77-108">HRESULT</span></span>|<span data-ttu-id="36d77-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="36d77-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36d77-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="36d77-110">S_OK</span></span>|<span data-ttu-id="36d77-111">`GetMaxThreads`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="36d77-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="36d77-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36d77-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36d77-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="36d77-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36d77-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36d77-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36d77-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="36d77-115">The call timed out.</span></span>|  
|<span data-ttu-id="36d77-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36d77-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36d77-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="36d77-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36d77-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36d77-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36d77-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="36d77-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36d77-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36d77-120">E_FAIL</span></span>|<span data-ttu-id="36d77-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="36d77-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36d77-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="36d77-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36d77-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="36d77-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="36d77-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="36d77-124">E_NOTIMPL</span></span>|<span data-ttu-id="36d77-125">O host não fornece uma implementação de `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="36d77-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36d77-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="36d77-126">Remarks</span></span>  
 <span data-ttu-id="36d77-127">Um host poderá controle exclusivo sobre o número de threads que podem ser alocadas para processar solicitações de e/s, por motivos como implementação, o desempenho ou a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="36d77-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="36d77-128">Por esse motivo, o host não é necessário para implementar `GetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="36d77-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="36d77-129">Nesse caso, o host deve retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="36d77-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d77-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36d77-130">Requirements</span></span>  
 <span data-ttu-id="36d77-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36d77-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d77-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36d77-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36d77-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="36d77-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36d77-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d77-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d77-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36d77-135">See Also</span></span>  
 [<span data-ttu-id="36d77-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="36d77-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="36d77-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="36d77-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
