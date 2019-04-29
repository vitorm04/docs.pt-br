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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796811"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="42971-102">Método IHostIoCompletionManager::SetCLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="42971-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="42971-103">Fornece o host com um ponteiro de interface para o [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instância implementada pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="42971-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42971-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42971-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42971-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42971-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="42971-106">[in] Um ponteiro de interface para um `ICLRIoCompletionManager` instância fornecida pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="42971-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42971-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="42971-107">Return Value</span></span>  
  
|<span data-ttu-id="42971-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42971-108">HRESULT</span></span>|<span data-ttu-id="42971-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="42971-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42971-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="42971-110">S_OK</span></span>|<span data-ttu-id="42971-111">`SetCLRIoCompletionManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="42971-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="42971-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42971-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42971-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="42971-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42971-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42971-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42971-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="42971-115">The call timed out.</span></span>|  
|<span data-ttu-id="42971-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42971-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42971-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="42971-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42971-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42971-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42971-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="42971-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42971-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42971-120">E_FAIL</span></span>|<span data-ttu-id="42971-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="42971-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42971-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="42971-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42971-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="42971-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42971-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="42971-124">Remarks</span></span>  
 <span data-ttu-id="42971-125">Depois que o CLR é chamado `SetCLRIoCompletionManager`, o host deve chamar [iclriocompletionmanager:: onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) para notificar o CLR, quando uma solicitação de e/s foi concluída.</span><span class="sxs-lookup"><span data-stu-id="42971-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42971-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42971-126">Requirements</span></span>  
 <span data-ttu-id="42971-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42971-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42971-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42971-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42971-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="42971-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42971-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42971-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42971-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42971-131">See also</span></span>

- [<span data-ttu-id="42971-132">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="42971-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="42971-133">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="42971-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
