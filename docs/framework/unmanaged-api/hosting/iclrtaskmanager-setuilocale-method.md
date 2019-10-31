---
title: Método ICLRTaskManager::SetUILocale
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: 051bd5cb846eb4e6e3390e17b3011a1c5b50bc45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127870"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="88a30-102">Método ICLRTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="88a30-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="88a30-103">Notifica o Common Language Runtime (CLR) que o host modificou a localidade da interface do usuário, ou cultura, na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="88a30-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a30-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88a30-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88a30-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88a30-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="88a30-106">no O valor do identificador de localidade que mapeia para a cultura geográfica e idioma atribuídos recentemente para a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="88a30-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88a30-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="88a30-107">Return Value</span></span>  
  
|<span data-ttu-id="88a30-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88a30-108">HRESULT</span></span>|<span data-ttu-id="88a30-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="88a30-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88a30-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="88a30-110">S_OK</span></span>|<span data-ttu-id="88a30-111">`SetUILocale` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="88a30-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="88a30-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88a30-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88a30-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="88a30-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="88a30-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="88a30-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="88a30-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="88a30-115">The call timed out.</span></span>|  
|<span data-ttu-id="88a30-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="88a30-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="88a30-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="88a30-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="88a30-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="88a30-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="88a30-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="88a30-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="88a30-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88a30-120">E_FAIL</span></span>|<span data-ttu-id="88a30-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="88a30-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="88a30-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="88a30-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="88a30-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="88a30-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88a30-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="88a30-124">Remarks</span></span>  
 <span data-ttu-id="88a30-125">`SetUILocale` fornece uma oportunidade para o host executar qualquer mecanismo que ele possa ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="88a30-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a30-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88a30-126">Requirements</span></span>  
 <span data-ttu-id="88a30-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88a30-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88a30-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="88a30-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88a30-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88a30-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88a30-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88a30-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a30-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88a30-131">See also</span></span>

- [<span data-ttu-id="88a30-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="88a30-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="88a30-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="88a30-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="88a30-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="88a30-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="88a30-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="88a30-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
