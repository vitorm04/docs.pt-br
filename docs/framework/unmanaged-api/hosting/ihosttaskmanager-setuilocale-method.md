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
ms.openlocfilehash: f929dceafc72af89cfd85b1617de7bbd0bc0dfff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442735"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="5d09e-102">Método IHostTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="5d09e-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="5d09e-103">Notifica o host que o common language runtime (CLR) alterou a localidade do usuário (UI) de interface ou cultura, a tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="5d09e-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d09e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d09e-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d09e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d09e-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="5d09e-106">[in] O valor do identificador de localidade que mapeia para o idioma e cultura geográfica recentemente atribuída.</span><span class="sxs-lookup"><span data-stu-id="5d09e-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d09e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5d09e-107">Return Value</span></span>  
  
|<span data-ttu-id="5d09e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d09e-108">HRESULT</span></span>|<span data-ttu-id="5d09e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d09e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d09e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d09e-110">S_OK</span></span>|<span data-ttu-id="5d09e-111">`SetUILocale` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="5d09e-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="5d09e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d09e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d09e-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5d09e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d09e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d09e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d09e-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="5d09e-115">The call timed out.</span></span>|  
|<span data-ttu-id="5d09e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d09e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d09e-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5d09e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d09e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d09e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d09e-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="5d09e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d09e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d09e-120">E_FAIL</span></span>|<span data-ttu-id="5d09e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5d09e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d09e-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="5d09e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d09e-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5d09e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5d09e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5d09e-124">E_NOTIMPL</span></span>|<span data-ttu-id="5d09e-125">O host não permite que o código de usuário gerenciado para alterar a cultura de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="5d09e-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d09e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d09e-126">Remarks</span></span>  
 <span data-ttu-id="5d09e-127">O tempo de execução chama `SetUILocale` quando o valor da <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> propriedade é alterada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5d09e-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="5d09e-128">Esse método fornece uma oportunidade para o host executar qualquer mecanismos pode ter para sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="5d09e-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="5d09e-129">Se um host não permite a localidade de interface do usuário a ser alterada de código gerenciado ou não implementa um mecanismo para sincronizar localidades, ele deverá retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="5d09e-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d09e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d09e-130">Requirements</span></span>  
 <span data-ttu-id="5d09e-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d09e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d09e-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d09e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d09e-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5d09e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d09e-134">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d09e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d09e-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d09e-135">See Also</span></span>  
 [<span data-ttu-id="5d09e-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="5d09e-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="5d09e-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="5d09e-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="5d09e-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="5d09e-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="5d09e-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="5d09e-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="5d09e-140">Método SetLocale</span><span class="sxs-lookup"><span data-stu-id="5d09e-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
