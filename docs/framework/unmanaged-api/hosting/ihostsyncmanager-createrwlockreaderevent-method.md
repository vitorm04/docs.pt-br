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
ms.openlocfilehash: c3e4095e0af13149a852ca055aa6a5e1e2d6848a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753403"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="0423c-102">Método IHostSyncManager::CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="0423c-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="0423c-103">Cria um objeto de evento de redefinição manual para a implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="0423c-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0423c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0423c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0423c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0423c-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="0423c-106">[in] `true`, se `ppEvent` deve ser sinalizado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0423c-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="0423c-107">[in] Um cookie para associar o bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="0423c-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="0423c-108">[out] Um ponteiro para o endereço de um [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) da instância ou nulo se não foi possível criar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="0423c-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0423c-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0423c-109">Return Value</span></span>  
  
|<span data-ttu-id="0423c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0423c-110">HRESULT</span></span>|<span data-ttu-id="0423c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0423c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0423c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0423c-112">S_OK</span></span>|<span data-ttu-id="0423c-113">`CreateRWLockReaderEvent` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0423c-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="0423c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0423c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0423c-115">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0423c-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0423c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0423c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0423c-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0423c-117">The call timed out.</span></span>|  
|<span data-ttu-id="0423c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0423c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0423c-119">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0423c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0423c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0423c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0423c-121">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="0423c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0423c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0423c-122">E_FAIL</span></span>|<span data-ttu-id="0423c-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0423c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0423c-124">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0423c-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0423c-125">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0423c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0423c-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0423c-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0423c-127">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="0423c-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0423c-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="0423c-128">Remarks</span></span>  
 <span data-ttu-id="0423c-129">O CLR chama `CreateRWLockReaderEvent` para obter uma referência a um `IHostManualEvent` instância a ser usada em sua implementação de um bloqueio de leitor.</span><span class="sxs-lookup"><span data-stu-id="0423c-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="0423c-130">O host pode usar o cookie para determinar quais tarefas estão aguardando o bloqueio de leitor, consultando o [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="0423c-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0423c-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0423c-131">Requirements</span></span>  
 <span data-ttu-id="0423c-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0423c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0423c-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0423c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0423c-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0423c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0423c-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0423c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0423c-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0423c-136">See also</span></span>

- [<span data-ttu-id="0423c-137">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="0423c-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0423c-138">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="0423c-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="0423c-139">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="0423c-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="0423c-140">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="0423c-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
