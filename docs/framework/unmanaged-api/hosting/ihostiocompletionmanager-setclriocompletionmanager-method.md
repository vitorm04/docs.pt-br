---
title: Método IHostIoCompletionManager::SetCLRIoCompletionManager
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: b84e92ca356ad83421d788a732926b614ffa4a8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133782"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="a49e1-102">Método IHostIoCompletionManager::SetCLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="a49e1-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="a49e1-103">Fornece ao host um ponteiro de interface para a instância [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) implementada pelo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a49e1-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a49e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a49e1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a49e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a49e1-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="a49e1-106">no Um ponteiro de interface para uma instância de `ICLRIoCompletionManager` fornecida pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="a49e1-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a49e1-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a49e1-107">Return Value</span></span>  
  
|<span data-ttu-id="a49e1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a49e1-108">HRESULT</span></span>|<span data-ttu-id="a49e1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a49e1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a49e1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a49e1-110">S_OK</span></span>|<span data-ttu-id="a49e1-111">`SetCLRIoCompletionManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a49e1-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="a49e1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a49e1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a49e1-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a49e1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a49e1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a49e1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a49e1-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a49e1-115">The call timed out.</span></span>|  
|<span data-ttu-id="a49e1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a49e1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a49e1-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a49e1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a49e1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a49e1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a49e1-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="a49e1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a49e1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a49e1-120">E_FAIL</span></span>|<span data-ttu-id="a49e1-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a49e1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a49e1-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="a49e1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a49e1-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a49e1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a49e1-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="a49e1-124">Remarks</span></span>  
 <span data-ttu-id="a49e1-125">Depois que o CLR tiver chamado `SetCLRIoCompletionManager`, o host deverá chamar [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) para notificar o CLR quando uma solicitação de e/s for concluída.</span><span class="sxs-lookup"><span data-stu-id="a49e1-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a49e1-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a49e1-126">Requirements</span></span>  
 <span data-ttu-id="a49e1-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a49e1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a49e1-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a49e1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a49e1-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a49e1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a49e1-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a49e1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a49e1-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a49e1-131">See also</span></span>

- [<span data-ttu-id="a49e1-132">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="a49e1-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a49e1-133">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="a49e1-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
