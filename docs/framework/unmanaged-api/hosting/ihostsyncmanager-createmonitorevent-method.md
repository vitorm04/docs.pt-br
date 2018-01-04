---
title: "Método IHostSyncManager::CreateMonitorEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateMonitorEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae12db71f4eae0f7d887fda26e05401f4f23ee5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="7b14a-102">Método IHostSyncManager::CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="7b14a-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="7b14a-103">Cria um objeto de evento de redefinição automática monitorado.</span><span class="sxs-lookup"><span data-stu-id="7b14a-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b14a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b14a-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b14a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b14a-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="7b14a-106">[in] Um cookie para associar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="7b14a-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="7b14a-107">[out] Um ponteiro para o endereço de um [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instância ou nulo se não foi possível criar o objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="7b14a-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b14a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7b14a-108">Return Value</span></span>  
  
|<span data-ttu-id="7b14a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b14a-109">HRESULT</span></span>|<span data-ttu-id="7b14a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b14a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b14a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b14a-111">S_OK</span></span>|<span data-ttu-id="7b14a-112">`CreateMonitorEvent`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="7b14a-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="7b14a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b14a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b14a-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7b14a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b14a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b14a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b14a-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="7b14a-116">The call timed out.</span></span>|  
|<span data-ttu-id="7b14a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b14a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b14a-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7b14a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b14a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b14a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b14a-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="7b14a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b14a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b14a-121">E_FAIL</span></span>|<span data-ttu-id="7b14a-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7b14a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b14a-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7b14a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b14a-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b14a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7b14a-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7b14a-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7b14a-126">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="7b14a-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b14a-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b14a-127">Remarks</span></span>  
 <span data-ttu-id="7b14a-128">`CreateMonitorEvent`Retorna um `IHostAutoEvent` que o CLR usa em sua implementação de gerenciado <xref:System.Threading.Monitor?displayProperty=nameWithType> tipo.</span><span class="sxs-lookup"><span data-stu-id="7b14a-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="7b14a-129">Esse método reflete o Win32 `CreateEvent` função, com um valor de `false` especificado para o `bManualReset` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7b14a-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="7b14a-130">O host pode usar o cookie para determinar qual tarefa está aguardando o monitor chamando o [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="7b14a-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b14a-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b14a-131">Requirements</span></span>  
 <span data-ttu-id="7b14a-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b14a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b14a-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7b14a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b14a-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7b14a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b14a-135">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b14a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b14a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b14a-136">See Also</span></span>  
 [<span data-ttu-id="7b14a-137">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="7b14a-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="7b14a-138">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="7b14a-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="7b14a-139">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="7b14a-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="7b14a-140">Monitores</span><span class="sxs-lookup"><span data-stu-id="7b14a-140">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)
