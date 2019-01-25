---
title: Método IHostSyncManager::CreateRWLockReaderEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e6a6e1d2aa90d4f113364693fb5f1e0399c21d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745448"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="f2993-102">Método IHostSyncManager::CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="f2993-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="f2993-103">Cria um objeto de evento de redefinição manual para a implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="f2993-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2993-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2993-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2993-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2993-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="f2993-106">[in] `true`, se `ppEvent` deve ser sinalizado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f2993-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="f2993-107">[in] Um cookie para associar o bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="f2993-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="f2993-108">[out] Um ponteiro para o endereço de um [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) da instância ou nulo se não foi possível criar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="f2993-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2993-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f2993-109">Return Value</span></span>  
  
|<span data-ttu-id="f2993-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2993-110">HRESULT</span></span>|<span data-ttu-id="f2993-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2993-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2993-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2993-112">S_OK</span></span>|<span data-ttu-id="f2993-113">`CreateRWLockReaderEvent` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f2993-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="f2993-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f2993-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2993-115">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f2993-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f2993-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f2993-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f2993-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f2993-117">The call timed out.</span></span>|  
|<span data-ttu-id="f2993-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f2993-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f2993-119">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f2993-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f2993-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f2993-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f2993-121">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="f2993-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f2993-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2993-122">E_FAIL</span></span>|<span data-ttu-id="f2993-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f2993-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f2993-124">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f2993-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f2993-125">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f2993-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f2993-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f2993-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f2993-127">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="f2993-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2993-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2993-128">Remarks</span></span>  
 <span data-ttu-id="f2993-129">O CLR chama `CreateRWLockReaderEvent` para obter uma referência a um `IHostManualEvent` instância a ser usada em sua implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="f2993-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="f2993-130">O host pode usar o cookie para determinar quais tarefas estão aguardando o bloqueio de leitor, consultando o [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f2993-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2993-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2993-131">Requirements</span></span>  
 <span data-ttu-id="f2993-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2993-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2993-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f2993-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2993-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f2993-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2993-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2993-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2993-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2993-136">See also</span></span>
- [<span data-ttu-id="f2993-137">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="f2993-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f2993-138">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="f2993-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="f2993-139">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="f2993-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="f2993-140">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="f2993-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
