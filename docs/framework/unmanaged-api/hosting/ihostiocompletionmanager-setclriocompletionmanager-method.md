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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd48664c78e3f5772cdfa655ebbc7cfa716f4950
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107185"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="1dd0e-102">Método IHostIoCompletionManager::SetCLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1dd0e-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="1dd0e-103">Fornece o host com um ponteiro de interface para o [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instância implementada pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1dd0e-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1dd0e-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd0e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1dd0e-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="1dd0e-106">[in] Um ponteiro de interface para um `ICLRIoCompletionManager` instância fornecida pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dd0e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1dd0e-107">Return Value</span></span>  
  
|<span data-ttu-id="1dd0e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dd0e-108">HRESULT</span></span>|<span data-ttu-id="1dd0e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dd0e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1dd0e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1dd0e-110">S_OK</span></span>|<span data-ttu-id="1dd0e-111">`SetCLRIoCompletionManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="1dd0e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1dd0e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1dd0e-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1dd0e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1dd0e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1dd0e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-115">The call timed out.</span></span>|  
|<span data-ttu-id="1dd0e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1dd0e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1dd0e-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1dd0e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1dd0e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1dd0e-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1dd0e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1dd0e-120">E_FAIL</span></span>|<span data-ttu-id="1dd0e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1dd0e-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1dd0e-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dd0e-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="1dd0e-124">Remarks</span></span>  
 <span data-ttu-id="1dd0e-125">Depois que o CLR é chamado `SetCLRIoCompletionManager`, o host deve chamar [iclriocompletionmanager:: onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) para notificar o CLR, quando uma solicitação de e/s foi concluída.</span><span class="sxs-lookup"><span data-stu-id="1dd0e-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd0e-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1dd0e-126">Requirements</span></span>  
 <span data-ttu-id="1dd0e-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd0e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd0e-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1dd0e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dd0e-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1dd0e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd0e-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd0e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd0e-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dd0e-131">See also</span></span>

- [<span data-ttu-id="1dd0e-132">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1dd0e-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1dd0e-133">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1dd0e-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
