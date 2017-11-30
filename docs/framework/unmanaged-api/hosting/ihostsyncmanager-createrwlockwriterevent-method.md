---
title: "Método IHostSyncManager::CreateRWLockWriterEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockWriterEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c89dec681102f96f96f1d7f3e802ded0a2df7b4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="8ebbc-102">Método IHostSyncManager::CreateRWLockWriterEvent</span><span class="sxs-lookup"><span data-stu-id="8ebbc-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="8ebbc-103">Cria um objeto de evento de redefinição automática para a implementação de um bloqueio de gravador.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ebbc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ebbc-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ebbc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ebbc-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="8ebbc-106">[in] Um cookie para associar o evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="8ebbc-107">[out] Um ponteiro para o endereço de um [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instância ou nulo se não foi possível criar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ebbc-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8ebbc-108">Return Value</span></span>  
  
|<span data-ttu-id="8ebbc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ebbc-109">HRESULT</span></span>|<span data-ttu-id="8ebbc-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ebbc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ebbc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ebbc-111">S_OK</span></span>|<span data-ttu-id="8ebbc-112">`CreateRWLockWriterEvent`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="8ebbc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ebbc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ebbc-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ebbc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ebbc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ebbc-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-116">The call timed out.</span></span>|  
|<span data-ttu-id="8ebbc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ebbc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ebbc-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ebbc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ebbc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ebbc-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ebbc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ebbc-121">E_FAIL</span></span>|<span data-ttu-id="8ebbc-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ebbc-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ebbc-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8ebbc-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8ebbc-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8ebbc-126">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ebbc-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ebbc-127">Remarks</span></span>  
 <span data-ttu-id="8ebbc-128">O CLR chama o `CreateRWLockWriterEvent` método para obter uma referência a um `IHostAutoEvent` instância para usar em sua implementação de um bloqueio de gravador.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="8ebbc-129">O host pode usar o cookie especificado para determinar quais tarefas estão aguardando o bloqueio chamando os métodos de iteração do [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="8ebbc-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ebbc-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ebbc-130">Requirements</span></span>  
 <span data-ttu-id="8ebbc-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ebbc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ebbc-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ebbc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ebbc-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8ebbc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ebbc-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ebbc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ebbc-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ebbc-135">See Also</span></span>  
 [<span data-ttu-id="8ebbc-136">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="8ebbc-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="8ebbc-137">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="8ebbc-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="8ebbc-138">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="8ebbc-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="8ebbc-139">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="8ebbc-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
