---
title: Método IHostTaskManager::SetCLRTaskManager
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a93efc0701248f8e4ef930261b31b3ce948647a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484921"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="5ab57-102">Método IHostTaskManager::SetCLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="5ab57-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="5ab57-103">Fornece o host com um ponteiro de interface para um [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instância implementada pelo common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5ab57-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab57-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ab57-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ab57-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ab57-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="5ab57-106">[in] Um ponteiro para um `ICLRTaskManager` instância implementada pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="5ab57-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ab57-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5ab57-107">Return Value</span></span>  
  
|<span data-ttu-id="5ab57-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ab57-108">HRESULT</span></span>|<span data-ttu-id="5ab57-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ab57-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ab57-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ab57-110">S_OK</span></span>|<span data-ttu-id="5ab57-111">`SetCLRTaskManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5ab57-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="5ab57-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ab57-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ab57-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5ab57-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ab57-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ab57-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ab57-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5ab57-115">The call timed out.</span></span>|  
|<span data-ttu-id="5ab57-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ab57-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ab57-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5ab57-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ab57-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ab57-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ab57-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="5ab57-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ab57-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ab57-120">E_FAIL</span></span>|<span data-ttu-id="5ab57-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5ab57-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ab57-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="5ab57-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ab57-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5ab57-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ab57-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ab57-124">Remarks</span></span>  
 <span data-ttu-id="5ab57-125">A tempo de execução chama `SetCLRTaskManager` para fornecer o host com um ponteiro de interface para um `ICLRTaskManager` instância.</span><span class="sxs-lookup"><span data-stu-id="5ab57-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ab57-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ab57-126">Requirements</span></span>  
 <span data-ttu-id="5ab57-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ab57-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab57-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ab57-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ab57-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5ab57-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ab57-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab57-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab57-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ab57-131">See also</span></span>
- [<span data-ttu-id="5ab57-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="5ab57-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5ab57-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="5ab57-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5ab57-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="5ab57-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5ab57-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="5ab57-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
