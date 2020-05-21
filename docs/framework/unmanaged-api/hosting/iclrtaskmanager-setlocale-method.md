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
ms.openlocfilehash: 8f316d91aab4c3862a0ad45b41539a4b80791ab9
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762782"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="89e80-102">Método ICLRTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="89e80-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="89e80-103">Notifica o Common Language Runtime (CLR) que o host modificou o valor do identificador de localidade (que é mapeado para a cultura geográfica e idioma) na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="89e80-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89e80-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89e80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89e80-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="89e80-106">no O valor do identificador de localidade que mapeia para a cultura geográfica e a linguagem recém atribuídas.</span><span class="sxs-lookup"><span data-stu-id="89e80-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89e80-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="89e80-107">Return Value</span></span>  
  
|<span data-ttu-id="89e80-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89e80-108">HRESULT</span></span>|<span data-ttu-id="89e80-109">Description</span><span class="sxs-lookup"><span data-stu-id="89e80-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89e80-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="89e80-110">S_OK</span></span>|<span data-ttu-id="89e80-111">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="89e80-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="89e80-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="89e80-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="89e80-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="89e80-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="89e80-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="89e80-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="89e80-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="89e80-115">The call timed out.</span></span>|  
|<span data-ttu-id="89e80-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="89e80-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="89e80-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="89e80-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="89e80-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="89e80-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="89e80-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="89e80-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="89e80-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="89e80-120">E_FAIL</span></span>|<span data-ttu-id="89e80-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="89e80-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="89e80-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="89e80-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="89e80-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="89e80-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89e80-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="89e80-124">Remarks</span></span>  
 <span data-ttu-id="89e80-125">`SetLocale`Dá ao host uma oportunidade de executar qualquer mecanismo que ele possa ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="89e80-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e80-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89e80-126">Requirements</span></span>  
 <span data-ttu-id="89e80-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89e80-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e80-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="89e80-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89e80-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89e80-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89e80-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e80-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e80-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="89e80-131">See also</span></span>

- [<span data-ttu-id="89e80-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="89e80-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="89e80-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="89e80-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="89e80-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="89e80-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="89e80-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="89e80-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
