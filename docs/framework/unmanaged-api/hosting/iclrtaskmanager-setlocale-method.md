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
ms.openlocfilehash: 79f24b3ccacd84037042a883d3a034bb7b4d200a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092084"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="5152d-102">Método ICLRTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="5152d-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="5152d-103">Notifica o Common Language Runtime (CLR) que o host modificou o valor do identificador de localidade (que é mapeado para a cultura geográfica e idioma) na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="5152d-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5152d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5152d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5152d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5152d-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="5152d-106">no O valor do identificador de localidade que mapeia para a cultura geográfica e a linguagem recém atribuídas.</span><span class="sxs-lookup"><span data-stu-id="5152d-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5152d-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5152d-107">Return Value</span></span>  
  
|<span data-ttu-id="5152d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5152d-108">HRESULT</span></span>|<span data-ttu-id="5152d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5152d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5152d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5152d-110">S_OK</span></span>|<span data-ttu-id="5152d-111">O método retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="5152d-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="5152d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5152d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5152d-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5152d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5152d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5152d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5152d-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5152d-115">The call timed out.</span></span>|  
|<span data-ttu-id="5152d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5152d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5152d-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5152d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5152d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5152d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5152d-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="5152d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5152d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5152d-120">E_FAIL</span></span>|<span data-ttu-id="5152d-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5152d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5152d-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="5152d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5152d-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5152d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5152d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="5152d-124">Remarks</span></span>  
 <span data-ttu-id="5152d-125">`SetLocale` dá ao host uma oportunidade de executar qualquer mecanismo que ele possa ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="5152d-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5152d-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5152d-126">Requirements</span></span>  
 <span data-ttu-id="5152d-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5152d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5152d-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5152d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5152d-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5152d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5152d-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5152d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5152d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5152d-131">See also</span></span>

- [<span data-ttu-id="5152d-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="5152d-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5152d-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="5152d-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5152d-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="5152d-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5152d-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="5152d-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
