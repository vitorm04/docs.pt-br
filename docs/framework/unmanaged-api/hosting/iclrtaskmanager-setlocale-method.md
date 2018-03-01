---
title: "Método ICLRTaskManager::SetLocale"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bbed6bff52d7ccad38eb45d12a31d08dc8b1b774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="44c17-102">Método ICLRTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="44c17-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="44c17-103">Notifica o common language runtime (CLR) que o host tiver modificado o valor do identificador de localidade (que é mapeado para a cultura geográfica e o idioma) da tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="44c17-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44c17-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44c17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44c17-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="44c17-106">[in] O valor do identificador de localidade que mapeia para o idioma e cultura geográfica recentemente atribuída.</span><span class="sxs-lookup"><span data-stu-id="44c17-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44c17-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="44c17-107">Return Value</span></span>  
  
|<span data-ttu-id="44c17-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44c17-108">HRESULT</span></span>|<span data-ttu-id="44c17-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="44c17-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44c17-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="44c17-110">S_OK</span></span>|<span data-ttu-id="44c17-111">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="44c17-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="44c17-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44c17-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44c17-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="44c17-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44c17-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44c17-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44c17-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="44c17-115">The call timed out.</span></span>|  
|<span data-ttu-id="44c17-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44c17-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44c17-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="44c17-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44c17-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44c17-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44c17-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="44c17-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44c17-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44c17-120">E_FAIL</span></span>|<span data-ttu-id="44c17-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="44c17-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44c17-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="44c17-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44c17-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44c17-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44c17-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="44c17-124">Remarks</span></span>  
 <span data-ttu-id="44c17-125">`SetLocale`o host uma oportunidade para executar qualquer mecanismos pode ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="44c17-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44c17-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44c17-126">Requirements</span></span>  
 <span data-ttu-id="44c17-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44c17-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44c17-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44c17-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44c17-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="44c17-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44c17-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44c17-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c17-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44c17-131">See Also</span></span>  
 [<span data-ttu-id="44c17-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="44c17-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="44c17-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="44c17-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="44c17-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="44c17-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="44c17-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="44c17-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
