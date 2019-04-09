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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e110f1f5ea326c232c7c96bb05913080e950083d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158893"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="eafe5-102">Método IHostTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="eafe5-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="eafe5-103">Notifica o host que o common language runtime (CLR) foi alterado, a localidade do usuário (UI) de interface ou cultura, a tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="eafe5-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eafe5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eafe5-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eafe5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eafe5-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="eafe5-106">[in] O valor do identificador de localidade que é mapeado para a cultura geográfica recentemente atribuída e o idioma.</span><span class="sxs-lookup"><span data-stu-id="eafe5-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eafe5-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="eafe5-107">Return Value</span></span>  
  
|<span data-ttu-id="eafe5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eafe5-108">HRESULT</span></span>|<span data-ttu-id="eafe5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="eafe5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eafe5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eafe5-110">S_OK</span></span>|`SetUILocale` <span data-ttu-id="eafe5-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="eafe5-111">returned successfully.</span></span>|  
|<span data-ttu-id="eafe5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eafe5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eafe5-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="eafe5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eafe5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eafe5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eafe5-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="eafe5-115">The call timed out.</span></span>|  
|<span data-ttu-id="eafe5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eafe5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eafe5-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="eafe5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eafe5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eafe5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eafe5-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="eafe5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eafe5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eafe5-120">E_FAIL</span></span>|<span data-ttu-id="eafe5-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="eafe5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eafe5-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="eafe5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eafe5-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eafe5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eafe5-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="eafe5-124">E_NOTIMPL</span></span>|<span data-ttu-id="eafe5-125">O host não permite código de usuário gerenciado para alterar a cultura de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="eafe5-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eafe5-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="eafe5-126">Remarks</span></span>  
 <span data-ttu-id="eafe5-127">A tempo de execução chama `SetUILocale` quando o valor da <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> propriedade é alterada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="eafe5-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="eafe5-128">Esse método fornece uma oportunidade para o host executar os mecanismos que ele pode ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="eafe5-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="eafe5-129">Se um host não permite que a localidade da interface do usuário a ser alterado a partir do código gerenciado ou não implementa um mecanismo para sincronizar as localidades, ele deverá retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="eafe5-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eafe5-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eafe5-130">Requirements</span></span>  
 <span data-ttu-id="eafe5-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eafe5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eafe5-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eafe5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eafe5-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="eafe5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="eafe5-134">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="eafe5-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eafe5-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eafe5-135">See also</span></span>

- [<span data-ttu-id="eafe5-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="eafe5-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="eafe5-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="eafe5-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="eafe5-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="eafe5-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="eafe5-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="eafe5-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="eafe5-140">Método SetLocale</span><span class="sxs-lookup"><span data-stu-id="eafe5-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
