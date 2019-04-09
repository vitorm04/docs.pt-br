---
title: Método ICLROnEventManager::UnregisterActionOnEvent
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54abd54662d4e99881dddf15876b596a4a705f70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108895"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="01706-102">Método ICLROnEventManager::UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="01706-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="01706-103">Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="01706-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01706-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01706-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01706-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01706-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="01706-106">[in] Um dos [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) valores, que indica o evento para o qual cancelar o registro o ponteiro de retorno de chamada descrito pelo `pAction`.</span><span class="sxs-lookup"><span data-stu-id="01706-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="01706-107">[in] Um ponteiro para um [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) objeto que foi passado como um parâmetro para o [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="01706-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01706-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="01706-108">Return Value</span></span>  
  
|<span data-ttu-id="01706-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01706-109">HRESULT</span></span>|<span data-ttu-id="01706-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="01706-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01706-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="01706-111">S_OK</span></span>|`UnregisterActionOnEvent` <span data-ttu-id="01706-112">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="01706-112">returned successfully.</span></span>|  
|<span data-ttu-id="01706-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01706-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01706-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="01706-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01706-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01706-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01706-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="01706-116">The call timed out.</span></span>|  
|<span data-ttu-id="01706-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01706-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01706-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="01706-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01706-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01706-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01706-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="01706-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01706-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01706-121">E_FAIL</span></span>|<span data-ttu-id="01706-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="01706-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01706-123">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="01706-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01706-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="01706-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01706-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01706-125">Requirements</span></span>  
 <span data-ttu-id="01706-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01706-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01706-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01706-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01706-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="01706-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="01706-129">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="01706-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01706-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01706-130">See also</span></span>

- [<span data-ttu-id="01706-131">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="01706-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="01706-132">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="01706-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="01706-133">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="01706-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="01706-134">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="01706-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
