---
title: "Método ICLRTaskManager::SetUILocale"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.SetUILocale
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fab9da8f7e63ad000595378f5bc36f3aadc2ac3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="796e4-102">Método ICLRTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="796e4-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="796e4-103">Notifica o common language runtime (CLR) que o host tiver modificado a localidade de interface do usuário ou a cultura, a tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="796e4-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="796e4-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="796e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="796e4-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="796e4-106">[in] O valor do identificador de localidade que mapeia para a cultura geográfica recentemente atribuída e o idioma da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="796e4-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="796e4-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="796e4-107">Return Value</span></span>  
  
|<span data-ttu-id="796e4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="796e4-108">HRESULT</span></span>|<span data-ttu-id="796e4-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="796e4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="796e4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="796e4-110">S_OK</span></span>|<span data-ttu-id="796e4-111">`SetUILocale`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="796e4-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="796e4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="796e4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="796e4-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="796e4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="796e4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="796e4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="796e4-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="796e4-115">The call timed out.</span></span>|  
|<span data-ttu-id="796e4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="796e4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="796e4-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="796e4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="796e4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="796e4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="796e4-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="796e4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="796e4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="796e4-120">E_FAIL</span></span>|<span data-ttu-id="796e4-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="796e4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="796e4-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="796e4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="796e4-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="796e4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="796e4-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="796e4-124">Remarks</span></span>  
 <span data-ttu-id="796e4-125">`SetUILocale`Fornece uma oportunidade para o host executar qualquer mecanismos pode ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="796e4-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="796e4-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="796e4-126">Requirements</span></span>  
 <span data-ttu-id="796e4-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="796e4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="796e4-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="796e4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="796e4-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="796e4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="796e4-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="796e4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796e4-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="796e4-131">See Also</span></span>  
 [<span data-ttu-id="796e4-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="796e4-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="796e4-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="796e4-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="796e4-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="796e4-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="796e4-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="796e4-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
