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
ms.openlocfilehash: a3018d8477d5abd7d03ad8675503624d2e44e8f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504128"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="57339-102">Método ICLROnEventManager::UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="57339-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="57339-103">Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="57339-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57339-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57339-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57339-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57339-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="57339-106">no Um dos valores de [EClrEvent](eclrevent-enumeration.md) , indicando o evento para o qual cancelar o registro do ponteiro de retorno de chamada descrito por `pAction` .</span><span class="sxs-lookup"><span data-stu-id="57339-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="57339-107">no Um ponteiro para um objeto [IActionOnCLREvent](iactiononclrevent-interface.md) que foi passado como um parâmetro para o método [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="57339-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57339-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="57339-108">Return Value</span></span>  
  
|<span data-ttu-id="57339-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57339-109">HRESULT</span></span>|<span data-ttu-id="57339-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="57339-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57339-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="57339-111">S_OK</span></span>|<span data-ttu-id="57339-112">`UnregisterActionOnEvent`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="57339-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="57339-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57339-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57339-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="57339-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57339-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57339-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57339-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="57339-116">The call timed out.</span></span>|  
|<span data-ttu-id="57339-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57339-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57339-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="57339-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57339-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57339-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57339-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="57339-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57339-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57339-121">E_FAIL</span></span>|<span data-ttu-id="57339-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="57339-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57339-123">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="57339-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57339-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57339-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57339-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57339-125">Requirements</span></span>  
 <span data-ttu-id="57339-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57339-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57339-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57339-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57339-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="57339-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57339-129">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57339-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57339-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="57339-130">See also</span></span>

- [<span data-ttu-id="57339-131">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="57339-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="57339-132">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="57339-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="57339-133">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="57339-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="57339-134">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="57339-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
