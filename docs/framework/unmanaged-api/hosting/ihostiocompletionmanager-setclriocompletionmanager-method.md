---
title: "Método IHostIoCompletionManager::SetCLRIoCompletionManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetCLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fde1045fd0f15e7255a163c1f1b041800e85921
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="12f18-102">Método IHostIoCompletionManager::SetCLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="12f18-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="12f18-103">Fornece o host com um ponteiro de interface para o [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instância implementada pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="12f18-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f18-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12f18-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12f18-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12f18-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="12f18-106">[in] Um ponteiro de interface para um `ICLRIoCompletionManager` instância fornecida pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="12f18-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12f18-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="12f18-107">Return Value</span></span>  
  
|<span data-ttu-id="12f18-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12f18-108">HRESULT</span></span>|<span data-ttu-id="12f18-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="12f18-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12f18-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="12f18-110">S_OK</span></span>|<span data-ttu-id="12f18-111">`SetCLRIoCompletionManager`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="12f18-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="12f18-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12f18-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12f18-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="12f18-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="12f18-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="12f18-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="12f18-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="12f18-115">The call timed out.</span></span>|  
|<span data-ttu-id="12f18-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="12f18-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="12f18-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="12f18-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="12f18-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="12f18-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="12f18-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="12f18-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="12f18-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12f18-120">E_FAIL</span></span>|<span data-ttu-id="12f18-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="12f18-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="12f18-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="12f18-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="12f18-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="12f18-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12f18-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="12f18-124">Remarks</span></span>  
 <span data-ttu-id="12f18-125">Depois que o CLR tem chamado `SetCLRIoCompletionManager`, o host deve chamar [Iclriocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) para notificar o CLR quando uma solicitação de e/s foi concluída.</span><span class="sxs-lookup"><span data-stu-id="12f18-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f18-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12f18-126">Requirements</span></span>  
 <span data-ttu-id="12f18-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f18-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f18-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="12f18-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12f18-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="12f18-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12f18-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f18-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f18-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12f18-131">See Also</span></span>  
 [<span data-ttu-id="12f18-132">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="12f18-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="12f18-133">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="12f18-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
