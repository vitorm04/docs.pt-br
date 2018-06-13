---
title: Método ICLRTaskManager::SetLocale
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab6b13c6b7dba34f5ea82d05f483b36bf96aab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437320"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="582a4-102">Método ICLRTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="582a4-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="582a4-103">Notifica o common language runtime (CLR) que o host tiver modificado o valor do identificador de localidade (que é mapeado para a cultura geográfica e o idioma) da tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="582a4-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="582a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="582a4-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="582a4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="582a4-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="582a4-106">[in] O valor do identificador de localidade que mapeia para o idioma e cultura geográfica recentemente atribuída.</span><span class="sxs-lookup"><span data-stu-id="582a4-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="582a4-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="582a4-107">Return Value</span></span>  
  
|<span data-ttu-id="582a4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="582a4-108">HRESULT</span></span>|<span data-ttu-id="582a4-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="582a4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="582a4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="582a4-110">S_OK</span></span>|<span data-ttu-id="582a4-111">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="582a4-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="582a4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="582a4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="582a4-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="582a4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="582a4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="582a4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="582a4-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="582a4-115">The call timed out.</span></span>|  
|<span data-ttu-id="582a4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="582a4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="582a4-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="582a4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="582a4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="582a4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="582a4-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="582a4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="582a4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="582a4-120">E_FAIL</span></span>|<span data-ttu-id="582a4-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="582a4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="582a4-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="582a4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="582a4-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="582a4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="582a4-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="582a4-124">Remarks</span></span>  
 <span data-ttu-id="582a4-125">`SetLocale` o host uma oportunidade para executar qualquer mecanismos pode ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="582a4-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="582a4-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="582a4-126">Requirements</span></span>  
 <span data-ttu-id="582a4-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="582a4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="582a4-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="582a4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="582a4-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="582a4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="582a4-130">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="582a4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582a4-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="582a4-131">See Also</span></span>  
 [<span data-ttu-id="582a4-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="582a4-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="582a4-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="582a4-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="582a4-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="582a4-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="582a4-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="582a4-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
