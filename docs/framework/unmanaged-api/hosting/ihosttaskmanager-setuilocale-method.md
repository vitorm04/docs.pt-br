---
title: "Método IHostTaskManager::SetUILocale"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetUILocale
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c29687d430187577ac25d8d2a007785632989ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="7580d-102">Método IHostTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="7580d-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="7580d-103">Notifica o host que o common language runtime (CLR) alterou a localidade do usuário (UI) de interface ou cultura, a tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="7580d-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7580d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7580d-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7580d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7580d-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="7580d-106">[in] O valor do identificador de localidade que mapeia para o idioma e cultura geográfica recentemente atribuída.</span><span class="sxs-lookup"><span data-stu-id="7580d-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7580d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7580d-107">Return Value</span></span>  
  
|<span data-ttu-id="7580d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7580d-108">HRESULT</span></span>|<span data-ttu-id="7580d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7580d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7580d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7580d-110">S_OK</span></span>|<span data-ttu-id="7580d-111">`SetUILocale`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="7580d-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="7580d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7580d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7580d-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7580d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7580d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7580d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7580d-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="7580d-115">The call timed out.</span></span>|  
|<span data-ttu-id="7580d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7580d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7580d-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7580d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7580d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7580d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7580d-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="7580d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7580d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7580d-120">E_FAIL</span></span>|<span data-ttu-id="7580d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7580d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7580d-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7580d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7580d-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7580d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7580d-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="7580d-124">E_NOTIMPL</span></span>|<span data-ttu-id="7580d-125">O host não permite que o código de usuário gerenciado para alterar a cultura de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7580d-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7580d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="7580d-126">Remarks</span></span>  
 <span data-ttu-id="7580d-127">O tempo de execução chama `SetUILocale` quando o valor da <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> propriedade é alterada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7580d-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="7580d-128">Esse método fornece uma oportunidade para o host executar qualquer mecanismos pode ter para sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="7580d-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="7580d-129">Se um host não permite a localidade de interface do usuário a ser alterada de código gerenciado ou não implementa um mecanismo para sincronizar localidades, ele deverá retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="7580d-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7580d-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7580d-130">Requirements</span></span>  
 <span data-ttu-id="7580d-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7580d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7580d-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7580d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7580d-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7580d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7580d-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7580d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7580d-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7580d-135">See Also</span></span>  
 [<span data-ttu-id="7580d-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7580d-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7580d-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7580d-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7580d-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7580d-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7580d-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7580d-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="7580d-140">Método SetLocale</span><span class="sxs-lookup"><span data-stu-id="7580d-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
