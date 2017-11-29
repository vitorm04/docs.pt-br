---
title: "Método IHostIoCompletionManager::CloseIoCompletionPort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CloseIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 066d51c821cf86522ffaca4c15db360ce96ed773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="ffc7d-102">Método IHostIoCompletionManager::CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="ffc7d-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="ffc7d-103">Solicita que o host fecha uma porta que foi aberta por meio de uma chamada anterior para [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="ffc7d-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffc7d-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffc7d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ffc7d-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="ffc7d-106">[in] O identificador da porta para fechar.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffc7d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ffc7d-107">Return Value</span></span>  
  
|<span data-ttu-id="ffc7d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffc7d-108">HRESULT</span></span>|<span data-ttu-id="ffc7d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffc7d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffc7d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffc7d-110">S_OK</span></span>|<span data-ttu-id="ffc7d-111">`CloseIoCompletionPort`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="ffc7d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffc7d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffc7d-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ffc7d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ffc7d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ffc7d-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-115">The call timed out.</span></span>|  
|<span data-ttu-id="ffc7d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ffc7d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ffc7d-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ffc7d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ffc7d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ffc7d-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ffc7d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffc7d-120">E_FAIL</span></span>|<span data-ttu-id="ffc7d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ffc7d-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ffc7d-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ffc7d-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ffc7d-124">E_INVALIDARG</span></span>|<span data-ttu-id="ffc7d-125">Um identificador de porta inválido foi passado.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffc7d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffc7d-126">Remarks</span></span>  
 <span data-ttu-id="ffc7d-127">`hPort`deve ser um identificador para uma porta que foi criado por uma chamada anterior para `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="ffc7d-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffc7d-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffc7d-128">Requirements</span></span>  
 <span data-ttu-id="ffc7d-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffc7d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffc7d-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffc7d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffc7d-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ffc7d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffc7d-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffc7d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc7d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffc7d-133">See Also</span></span>  
 [<span data-ttu-id="ffc7d-134">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="ffc7d-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="ffc7d-135">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="ffc7d-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
