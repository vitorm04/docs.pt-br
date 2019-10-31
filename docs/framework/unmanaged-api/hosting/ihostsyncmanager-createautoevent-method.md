---
title: Método IHostSyncManager::CreateAutoEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: b3778e12dd96d4f4653633252e13469601c4879d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139444"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="36e7c-102">Método IHostSyncManager::CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="36e7c-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="36e7c-103">Cria um objeto de evento de redefinição automática.</span><span class="sxs-lookup"><span data-stu-id="36e7c-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36e7c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36e7c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36e7c-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="36e7c-106">fora Um ponteiro para o endereço de uma instância de [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) implementada pelo host ou NULL se o objeto de evento não pôde ser criado.</span><span class="sxs-lookup"><span data-stu-id="36e7c-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36e7c-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="36e7c-107">Return Value</span></span>  
  
|<span data-ttu-id="36e7c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36e7c-108">HRESULT</span></span>|<span data-ttu-id="36e7c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="36e7c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36e7c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="36e7c-110">S_OK</span></span>|<span data-ttu-id="36e7c-111">`CreateAutoEvent` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="36e7c-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="36e7c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36e7c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36e7c-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="36e7c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36e7c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36e7c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36e7c-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="36e7c-115">The call timed out.</span></span>|  
|<span data-ttu-id="36e7c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36e7c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36e7c-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="36e7c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36e7c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36e7c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36e7c-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="36e7c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36e7c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36e7c-120">E_FAIL</span></span>|<span data-ttu-id="36e7c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="36e7c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36e7c-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="36e7c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36e7c-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="36e7c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="36e7c-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="36e7c-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="36e7c-125">Não havia memória suficiente disponível para criar o objeto de evento solicitado.</span><span class="sxs-lookup"><span data-stu-id="36e7c-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36e7c-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="36e7c-126">Remarks</span></span>  
 <span data-ttu-id="36e7c-127">`CreateAutoEvent` cria um objeto de evento automático cujo estado é alterado automaticamente para não sinalizado após o lançamento do thread em espera.</span><span class="sxs-lookup"><span data-stu-id="36e7c-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="36e7c-128">Esse método espelha a função de `CreateEvent` do Win32 com um valor de `false` especificado para o parâmetro `bManualReset`</span><span class="sxs-lookup"><span data-stu-id="36e7c-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36e7c-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36e7c-129">Requirements</span></span>  
 <span data-ttu-id="36e7c-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36e7c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36e7c-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="36e7c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36e7c-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="36e7c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36e7c-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36e7c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e7c-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36e7c-134">See also</span></span>

- [<span data-ttu-id="36e7c-135">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="36e7c-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="36e7c-136">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="36e7c-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="36e7c-137">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="36e7c-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="36e7c-138">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="36e7c-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
