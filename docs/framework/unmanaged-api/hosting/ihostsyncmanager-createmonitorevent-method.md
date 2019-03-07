---
title: Método IHostSyncManager::CreateMonitorEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99f2b7128ab984d023ce0aed73dd96167a661682
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497126"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="94b61-102">Método IHostSyncManager::CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="94b61-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="94b61-103">Cria um objeto de evento de redefinição automática monitorado.</span><span class="sxs-lookup"><span data-stu-id="94b61-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94b61-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94b61-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94b61-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="94b61-106">[in] Um cookie para associar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="94b61-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="94b61-107">[out] Um ponteiro para o endereço de um [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) da instância ou nulo se não foi possível criar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="94b61-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94b61-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="94b61-108">Return Value</span></span>  
  
|<span data-ttu-id="94b61-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94b61-109">HRESULT</span></span>|<span data-ttu-id="94b61-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="94b61-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94b61-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="94b61-111">S_OK</span></span>|<span data-ttu-id="94b61-112">`CreateMonitorEvent` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="94b61-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="94b61-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94b61-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94b61-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="94b61-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="94b61-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="94b61-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="94b61-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="94b61-116">The call timed out.</span></span>|  
|<span data-ttu-id="94b61-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="94b61-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="94b61-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="94b61-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="94b61-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="94b61-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="94b61-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="94b61-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="94b61-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94b61-121">E_FAIL</span></span>|<span data-ttu-id="94b61-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="94b61-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="94b61-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="94b61-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="94b61-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="94b61-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="94b61-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="94b61-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="94b61-126">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="94b61-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94b61-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="94b61-127">Remarks</span></span>  
 <span data-ttu-id="94b61-128">`CreateMonitorEvent` Retorna um `IHostAutoEvent` que o CLR usa em sua implementação de gerenciado <xref:System.Threading.Monitor?displayProperty=nameWithType> tipo.</span><span class="sxs-lookup"><span data-stu-id="94b61-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="94b61-129">Esse método espelha o Win32 `CreateEvent` função, com um valor de `false` especificado para o `bManualReset` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="94b61-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="94b61-130">O host pode usar o cookie para determinar qual tarefa está aguardando o monitor por meio da chamada a [iclrsyncmanager:: Getmonitorowner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="94b61-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94b61-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94b61-131">Requirements</span></span>  
 <span data-ttu-id="94b61-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94b61-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94b61-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94b61-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94b61-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="94b61-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94b61-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94b61-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b61-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94b61-136">See also</span></span>
- [<span data-ttu-id="94b61-137">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="94b61-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="94b61-138">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="94b61-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="94b61-139">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="94b61-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
