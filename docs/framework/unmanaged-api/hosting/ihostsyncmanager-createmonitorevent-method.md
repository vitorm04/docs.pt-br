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
ms.openlocfilehash: b934816073a48936afca119895488ddf2f0e37d2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199754"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="8e965-102">Método IHostSyncManager::CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="8e965-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="8e965-103">Cria um objeto de evento de redefinição automática monitorado.</span><span class="sxs-lookup"><span data-stu-id="8e965-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e965-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e965-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e965-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e965-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="8e965-106">[in] Um cookie para associar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="8e965-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="8e965-107">[out] Um ponteiro para o endereço de um [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) da instância ou nulo se não foi possível criar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="8e965-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e965-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8e965-108">Return Value</span></span>  
  
|<span data-ttu-id="8e965-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e965-109">HRESULT</span></span>|<span data-ttu-id="8e965-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e965-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e965-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e965-111">S_OK</span></span>|<span data-ttu-id="8e965-112">`CreateMonitorEvent` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8e965-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="8e965-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8e965-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8e965-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8e965-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8e965-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8e965-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8e965-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8e965-116">The call timed out.</span></span>|  
|<span data-ttu-id="8e965-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8e965-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8e965-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8e965-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8e965-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8e965-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8e965-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="8e965-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8e965-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8e965-121">E_FAIL</span></span>|<span data-ttu-id="8e965-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8e965-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8e965-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8e965-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8e965-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8e965-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8e965-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8e965-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8e965-126">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="8e965-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e965-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e965-127">Remarks</span></span>  
 <span data-ttu-id="8e965-128">`CreateMonitorEvent` Retorna um `IHostAutoEvent` que o CLR usa em sua implementação de gerenciado <xref:System.Threading.Monitor?displayProperty=nameWithType> tipo.</span><span class="sxs-lookup"><span data-stu-id="8e965-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="8e965-129">Esse método espelha o Win32 `CreateEvent` função, com um valor de `false` especificado para o `bManualReset` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8e965-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="8e965-130">O host pode usar o cookie para determinar qual tarefa está aguardando o monitor por meio da chamada a [iclrsyncmanager:: Getmonitorowner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8e965-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e965-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e965-131">Requirements</span></span>  
 <span data-ttu-id="8e965-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e965-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e965-133">**Cabeçalho:** mscoree. H</span><span class="sxs-lookup"><span data-stu-id="8e965-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e965-134">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8e965-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e965-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e965-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e965-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e965-136">See Also</span></span>  
 [<span data-ttu-id="8e965-137">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="8e965-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="8e965-138">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="8e965-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="8e965-139">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="8e965-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <xref:System.Threading.Monitor>
