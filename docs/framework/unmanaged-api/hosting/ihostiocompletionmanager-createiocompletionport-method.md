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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fc7bda648dd19f614eb27ff514da653dcd347fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619404"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="cd958-102">Método IHostIoCompletionManager::CreateIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="cd958-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="cd958-103">Solicita que o host, crie uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="cd958-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd958-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd958-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd958-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd958-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="cd958-106">[out] Um ponteiro para um identificador para a porta de conclusão de e/s recém-criado ou 0 (zero), se a porta não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="cd958-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd958-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cd958-107">Return Value</span></span>  
  
|<span data-ttu-id="cd958-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd958-108">HRESULT</span></span>|<span data-ttu-id="cd958-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd958-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd958-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd958-110">S_OK</span></span>|<span data-ttu-id="cd958-111">`CreateIoCompletionPort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="cd958-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="cd958-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd958-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd958-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="cd958-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd958-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd958-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd958-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="cd958-115">The call timed out.</span></span>|  
|<span data-ttu-id="cd958-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd958-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd958-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="cd958-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd958-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd958-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd958-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="cd958-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd958-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd958-120">E_FAIL</span></span>|<span data-ttu-id="cd958-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="cd958-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd958-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="cd958-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd958-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cd958-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cd958-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cd958-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cd958-125">Não havia memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="cd958-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd958-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd958-126">Remarks</span></span>  
 <span data-ttu-id="cd958-127">O CLR chama o `CreateIoCompletionPort` método para solicitar que o host, crie uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="cd958-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="cd958-128">Ele se vincula as operações de e/s para essa porta por meio de uma chamada para o [ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="cd958-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="cd958-129">O host relata o status novamente para o CLR, chamando [iclriocompletionmanager:: onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd958-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd958-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd958-130">Requirements</span></span>  
 <span data-ttu-id="cd958-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd958-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd958-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd958-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd958-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="cd958-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd958-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd958-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd958-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd958-135">See also</span></span>
- [<span data-ttu-id="cd958-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="cd958-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="cd958-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="cd958-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
