---
title: Método IHostIoCompletionManager::CreateIoCompletionPort
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: c3fa8aeebe529564c0ecc4a970f586fffc97ee05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133876"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="0f3f9-102">Método IHostIoCompletionManager::CreateIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="0f3f9-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="0f3f9-103">Solicita que o host crie uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f3f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f3f9-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f3f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f3f9-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="0f3f9-106">fora Um ponteiro para um identificador para a porta de conclusão de e/s recém-criada ou 0 (zero), se a porta não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f3f9-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0f3f9-107">Return Value</span></span>  
  
|<span data-ttu-id="0f3f9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f3f9-108">HRESULT</span></span>|<span data-ttu-id="0f3f9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f3f9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f3f9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f3f9-110">S_OK</span></span>|<span data-ttu-id="0f3f9-111">`CreateIoCompletionPort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="0f3f9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f3f9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f3f9-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f3f9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f3f9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f3f9-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-115">The call timed out.</span></span>|  
|<span data-ttu-id="0f3f9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f3f9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f3f9-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f3f9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f3f9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f3f9-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f3f9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f3f9-120">E_FAIL</span></span>|<span data-ttu-id="0f3f9-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f3f9-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f3f9-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0f3f9-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0f3f9-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0f3f9-125">Não havia memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f3f9-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f3f9-126">Remarks</span></span>  
 <span data-ttu-id="0f3f9-127">O CLR chama o método `CreateIoCompletionPort` para solicitar que o host crie uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="0f3f9-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="0f3f9-128">Ele associa as operações de e/s a essa porta por meio de uma chamada para o método [IHostIoCompletionManager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0f3f9-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="0f3f9-129">O host relata o status de volta para o CLR chamando [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="0f3f9-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f3f9-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f3f9-130">Requirements</span></span>  
 <span data-ttu-id="0f3f9-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f3f9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f3f9-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f3f9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f3f9-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0f3f9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f3f9-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f3f9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f3f9-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f3f9-135">See also</span></span>

- [<span data-ttu-id="0f3f9-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="0f3f9-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0f3f9-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="0f3f9-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
