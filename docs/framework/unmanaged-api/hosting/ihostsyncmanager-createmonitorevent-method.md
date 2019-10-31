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
ms.openlocfilehash: f7426585045c7ae81377ec9bfca9d397d6f734cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192016"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="69476-102">Método IHostSyncManager::CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="69476-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="69476-103">Cria um objeto de evento monitorado de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="69476-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69476-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69476-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69476-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69476-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="69476-106">no Um cookie a ser associado ao objeto de evento.</span><span class="sxs-lookup"><span data-stu-id="69476-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="69476-107">fora Um ponteiro para o endereço de uma instância de [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) ou NULL se o objeto de evento não pôde ser criado.</span><span class="sxs-lookup"><span data-stu-id="69476-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69476-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="69476-108">Return Value</span></span>  
  
|<span data-ttu-id="69476-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="69476-109">HRESULT</span></span>|<span data-ttu-id="69476-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="69476-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69476-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="69476-111">S_OK</span></span>|<span data-ttu-id="69476-112">`CreateMonitorEvent` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="69476-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="69476-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="69476-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="69476-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="69476-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="69476-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="69476-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="69476-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="69476-116">The call timed out.</span></span>|  
|<span data-ttu-id="69476-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="69476-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="69476-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="69476-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="69476-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="69476-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="69476-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="69476-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="69476-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="69476-121">E_FAIL</span></span>|<span data-ttu-id="69476-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="69476-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="69476-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="69476-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="69476-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="69476-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="69476-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="69476-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="69476-126">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="69476-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69476-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="69476-127">Remarks</span></span>  
 <span data-ttu-id="69476-128">`CreateMonitorEvent` retorna um `IHostAutoEvent` que o CLR usa em sua implementação do tipo de <xref:System.Threading.Monitor?displayProperty=nameWithType> gerenciado.</span><span class="sxs-lookup"><span data-stu-id="69476-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="69476-129">Esse método espelha a função de `CreateEvent` do Win32, com um valor de `false` especificado para o parâmetro `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="69476-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="69476-130">O host pode usar o cookie para determinar qual tarefa está aguardando no monitor chamando o método [ICLRSyncManager:: GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) .</span><span class="sxs-lookup"><span data-stu-id="69476-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69476-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69476-131">Requirements</span></span>  
 <span data-ttu-id="69476-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69476-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69476-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="69476-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69476-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="69476-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69476-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69476-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69476-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69476-136">See also</span></span>

- [<span data-ttu-id="69476-137">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="69476-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="69476-138">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="69476-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="69476-139">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="69476-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
