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
ms.openlocfilehash: 0e030a33a0a3368f35c82fad33f1ea2ce32446af
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841822"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="2525a-102">Método IHostTaskManager::SetCLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="2525a-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="2525a-103">Fornece ao host um ponteiro de interface para uma instância [ICLRTaskManager](iclrtaskmanager-interface.md) implementada pelo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2525a-103">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2525a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2525a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2525a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2525a-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="2525a-106">no Um ponteiro para uma `ICLRTaskManager` instância implementada pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="2525a-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2525a-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="2525a-107">Return Value</span></span>  
  
|<span data-ttu-id="2525a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2525a-108">HRESULT</span></span>|<span data-ttu-id="2525a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2525a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2525a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2525a-110">S_OK</span></span>|<span data-ttu-id="2525a-111">`SetCLRTaskManager`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2525a-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="2525a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2525a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2525a-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2525a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2525a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2525a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2525a-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2525a-115">The call timed out.</span></span>|  
|<span data-ttu-id="2525a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2525a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2525a-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2525a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2525a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2525a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2525a-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="2525a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2525a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2525a-120">E_FAIL</span></span>|<span data-ttu-id="2525a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2525a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2525a-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="2525a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2525a-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2525a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2525a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="2525a-124">Remarks</span></span>  
 <span data-ttu-id="2525a-125">O tempo de execução chama `SetCLRTaskManager` para fornecer ao host um ponteiro de interface para uma `ICLRTaskManager` instância.</span><span class="sxs-lookup"><span data-stu-id="2525a-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2525a-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2525a-126">Requirements</span></span>  
 <span data-ttu-id="2525a-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2525a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2525a-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2525a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2525a-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2525a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2525a-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2525a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2525a-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2525a-131">See also</span></span>

- [<span data-ttu-id="2525a-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="2525a-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2525a-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="2525a-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2525a-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="2525a-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2525a-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="2525a-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
