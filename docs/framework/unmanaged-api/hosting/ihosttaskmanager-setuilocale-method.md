---
title: Método IHostTaskManager::SetUILocale
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: a929a125fc8c70744246f4f96d8a09a4605f537c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132936"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="777dc-102">Método IHostTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="777dc-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="777dc-103">Notifica o host de que o Common Language Runtime (CLR) alterou a localidade da interface do usuário, ou cultura, na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="777dc-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="777dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="777dc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="777dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="777dc-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="777dc-106">no O valor do identificador de localidade que mapeia para a cultura geográfica e a linguagem recém atribuídas.</span><span class="sxs-lookup"><span data-stu-id="777dc-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="777dc-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="777dc-107">Return Value</span></span>  
  
|<span data-ttu-id="777dc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="777dc-108">HRESULT</span></span>|<span data-ttu-id="777dc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="777dc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="777dc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="777dc-110">S_OK</span></span>|<span data-ttu-id="777dc-111">`SetUILocale` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="777dc-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="777dc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="777dc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="777dc-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="777dc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="777dc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="777dc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="777dc-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="777dc-115">The call timed out.</span></span>|  
|<span data-ttu-id="777dc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="777dc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="777dc-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="777dc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="777dc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="777dc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="777dc-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="777dc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="777dc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="777dc-120">E_FAIL</span></span>|<span data-ttu-id="777dc-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="777dc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="777dc-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="777dc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="777dc-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="777dc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="777dc-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="777dc-124">E_NOTIMPL</span></span>|<span data-ttu-id="777dc-125">O host não permite que o código de usuário gerenciado altere a cultura da IU.</span><span class="sxs-lookup"><span data-stu-id="777dc-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="777dc-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="777dc-126">Remarks</span></span>  
 <span data-ttu-id="777dc-127">O tempo de execução chama `SetUILocale` quando o valor da propriedade <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> é alterado pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="777dc-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="777dc-128">Esse método fornece uma oportunidade para o host executar qualquer mecanismo que ele possa ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="777dc-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="777dc-129">Se um host não permitir que a localidade da interface do usuário seja alterada do código gerenciado ou não implementar um mecanismo para sincronizar as localidades, ele deverá retornar E_NOTIMPL a partir desse método.</span><span class="sxs-lookup"><span data-stu-id="777dc-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="777dc-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="777dc-130">Requirements</span></span>  
 <span data-ttu-id="777dc-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="777dc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="777dc-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="777dc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="777dc-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="777dc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="777dc-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="777dc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777dc-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="777dc-135">See also</span></span>

- [<span data-ttu-id="777dc-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="777dc-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="777dc-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="777dc-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="777dc-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="777dc-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="777dc-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="777dc-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="777dc-140">Método SetLocale</span><span class="sxs-lookup"><span data-stu-id="777dc-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
