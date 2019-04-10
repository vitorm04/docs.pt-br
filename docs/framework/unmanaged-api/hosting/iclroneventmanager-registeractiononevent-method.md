---
title: Método ICLROnEventManager::RegisterActionOnEvent
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68a8493a9eb5177844e81ef7a9612f979ffe89c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216483"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="7c113-102">Método ICLROnEventManager::RegisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="7c113-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="7c113-103">Registra um ponteiro de retorno de chamada para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="7c113-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c113-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c113-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c113-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c113-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="7c113-106">[in] Um dos [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) valores, que indica o evento para o qual registrar o ponteiro de retorno de chamada descrito pelo `pAction`.</span><span class="sxs-lookup"><span data-stu-id="7c113-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="7c113-107">[in] Um ponteiro para um [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) objeto que é chamado quando o evento registrado for acionado.</span><span class="sxs-lookup"><span data-stu-id="7c113-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c113-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7c113-108">Return Value</span></span>  
  
|<span data-ttu-id="7c113-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c113-109">HRESULT</span></span>|<span data-ttu-id="7c113-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c113-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c113-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c113-111">S_OK</span></span>|`RegisterActionOnEvent` <span data-ttu-id="7c113-112">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7c113-112">returned successfully.</span></span>|  
|<span data-ttu-id="7c113-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c113-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c113-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7c113-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c113-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c113-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c113-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7c113-116">The call timed out.</span></span>|  
|<span data-ttu-id="7c113-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c113-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c113-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7c113-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c113-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c113-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c113-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="7c113-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c113-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c113-121">E_FAIL</span></span>|<span data-ttu-id="7c113-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7c113-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c113-123">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7c113-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c113-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7c113-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c113-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c113-125">Remarks</span></span>  
 <span data-ttu-id="7c113-126">O host pode registrar retornos de chamada para um ou ambos os tipos de duas evento descritos pelo `EClrEvent`.</span><span class="sxs-lookup"><span data-stu-id="7c113-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="7c113-127">Obtém o host a `ICLROnEventManager` interface chamando o [iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="7c113-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c113-128">Os eventos que `RegisterActionOnEvent` registros podem ser acionados mais de uma vez e de diversos threads para sinalizar um descarregamento ou a desabilitação do CLR.</span><span class="sxs-lookup"><span data-stu-id="7c113-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c113-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c113-129">Requirements</span></span>  
 <span data-ttu-id="7c113-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c113-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c113-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c113-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c113-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7c113-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7c113-133">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7c113-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7c113-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c113-134">See also</span></span>

- [<span data-ttu-id="7c113-135">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="7c113-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="7c113-136">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="7c113-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="7c113-137">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="7c113-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="7c113-138">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="7c113-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
