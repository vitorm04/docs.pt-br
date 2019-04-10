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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b07b3649cc1d7fcc2c75cbbd59414ee67819103
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217920"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="c2883-102">Método IHostAutoEvent::Wait</span><span class="sxs-lookup"><span data-stu-id="c2883-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="c2883-103">Faz com que o atual [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instância aguardar até que ele é de propriedade ou uma quantidade especificada de tempo passa.</span><span class="sxs-lookup"><span data-stu-id="c2883-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2883-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2883-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2883-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2883-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="c2883-106">[in] O número de milissegundos atual `IHostAutoEvent` instância deve esperar antes de retornar, se nenhum thread ou fibra assume a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c2883-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="c2883-107">[in] Um dos [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores, especificando a ação que o host deve executar se este blocos de operação.</span><span class="sxs-lookup"><span data-stu-id="c2883-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2883-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c2883-108">Return Value</span></span>  
  
|<span data-ttu-id="c2883-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2883-109">HRESULT</span></span>|<span data-ttu-id="c2883-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2883-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2883-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2883-111">S_OK</span></span>|`Wait` <span data-ttu-id="c2883-112">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2883-112">returned successfully.</span></span>|  
|<span data-ttu-id="c2883-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2883-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2883-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2883-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2883-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2883-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2883-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c2883-116">The call timed out.</span></span>|  
|<span data-ttu-id="c2883-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2883-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2883-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c2883-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2883-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2883-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2883-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="c2883-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2883-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2883-121">E_FAIL</span></span>|<span data-ttu-id="c2883-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c2883-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2883-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c2883-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2883-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2883-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c2883-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="c2883-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="c2883-126">O host detectou um deadlock durante o intervalo de espera e escolheu o evento representado por atual `IHostAutoEvent` instância como a vítima de deadlock.</span><span class="sxs-lookup"><span data-stu-id="c2883-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2883-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2883-127">Requirements</span></span>  
 <span data-ttu-id="c2883-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2883-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2883-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2883-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2883-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c2883-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c2883-131">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c2883-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2883-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2883-132">See also</span></span>

- [<span data-ttu-id="c2883-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c2883-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c2883-134">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="c2883-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="c2883-135">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="c2883-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="c2883-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c2883-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
