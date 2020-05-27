---
title: Método IHostAutoEvent::Wait
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
ms.openlocfilehash: 7baabafc61e14d127ff3f0cdb7453be6f1a2abeb
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804968"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="9a386-102">Método IHostAutoEvent::Wait</span><span class="sxs-lookup"><span data-stu-id="9a386-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="9a386-103">Faz com que a instância de [IHostAutoEvent](ihostautoevent-interface.md) atual aguarde até que ela seja propriedade ou um período de tempo especificado decorre.</span><span class="sxs-lookup"><span data-stu-id="9a386-103">Causes the current [IHostAutoEvent](ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a386-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a386-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a386-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a386-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="9a386-106">no O número de milissegundos que a `IHostAutoEvent` instância atual deve aguardar antes de retornar, se nenhum thread ou fibra assumir a propriedade.</span><span class="sxs-lookup"><span data-stu-id="9a386-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="9a386-107">no Um dos valores de [WAIT_OPTION](wait-option-enumeration.md) , especificando a ação que o host deve executar se essa operação bloquear.</span><span class="sxs-lookup"><span data-stu-id="9a386-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a386-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="9a386-108">Return Value</span></span>  
  
|<span data-ttu-id="9a386-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a386-109">HRESULT</span></span>|<span data-ttu-id="9a386-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a386-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a386-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a386-111">S_OK</span></span>|<span data-ttu-id="9a386-112">`Wait`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9a386-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="9a386-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a386-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a386-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9a386-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a386-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a386-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a386-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9a386-116">The call timed out.</span></span>|  
|<span data-ttu-id="9a386-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a386-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a386-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9a386-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a386-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a386-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a386-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9a386-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a386-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a386-121">E_FAIL</span></span>|<span data-ttu-id="9a386-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9a386-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a386-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9a386-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a386-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9a386-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a386-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="9a386-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="9a386-126">O host detectou um deadlock durante o intervalo de espera e escolheu o evento representado pela `IHostAutoEvent` instância atual como a vítima do deadlock.</span><span class="sxs-lookup"><span data-stu-id="9a386-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a386-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a386-127">Requirements</span></span>  
 <span data-ttu-id="9a386-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a386-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a386-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a386-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a386-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a386-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a386-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a386-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a386-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a386-132">See also</span></span>

- [<span data-ttu-id="9a386-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="9a386-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="9a386-134">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="9a386-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="9a386-135">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="9a386-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="9a386-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="9a386-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
