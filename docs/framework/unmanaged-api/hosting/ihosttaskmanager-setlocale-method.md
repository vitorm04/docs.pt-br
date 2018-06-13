---
title: Método IHostTaskManager::SetLocale
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af9a8939c2ff50eb41b4f5c14097751fdc92ff83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443135"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="7e2c6-102">Método IHostTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="7e2c6-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="7e2c6-103">Notifica o host que o common language runtime (CLR) alterou a localidade ou cultura, a tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e2c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e2c6-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e2c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e2c6-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="7e2c6-106">[in] O valor do identificador de localidade que mapeia para o idioma e cultura geográfica recentemente atribuída.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e2c6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7e2c6-107">Return Value</span></span>  
  
|<span data-ttu-id="7e2c6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e2c6-108">HRESULT</span></span>|<span data-ttu-id="7e2c6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e2c6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e2c6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e2c6-110">S_OK</span></span>|<span data-ttu-id="7e2c6-111">`SetLocale` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="7e2c6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7e2c6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7e2c6-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7e2c6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7e2c6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7e2c6-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-115">The call timed out.</span></span>|  
|<span data-ttu-id="7e2c6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7e2c6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7e2c6-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7e2c6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7e2c6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7e2c6-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7e2c6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7e2c6-120">E_FAIL</span></span>|<span data-ttu-id="7e2c6-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7e2c6-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7e2c6-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7e2c6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="7e2c6-124">E_NOTIMPL</span></span>|<span data-ttu-id="7e2c6-125">O host não permite que o código de usuário gerenciado modificar a localidade.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e2c6-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e2c6-126">Remarks</span></span>  
 <span data-ttu-id="7e2c6-127">O tempo de execução chama `SetLocale` quando o valor da <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriedade é alterada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="7e2c6-128">Esse método fornece uma oportunidade para o host executar qualquer mecanismos pode ter para sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="7e2c6-129">Se um host não permite a localidade a ser alterada de código gerenciado ou não implementa um mecanismo para sincronizar localidades, ele deverá retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="7e2c6-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e2c6-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e2c6-130">Requirements</span></span>  
 <span data-ttu-id="7e2c6-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e2c6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e2c6-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e2c6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e2c6-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7e2c6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e2c6-134">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e2c6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2c6-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e2c6-135">See Also</span></span>  
 [<span data-ttu-id="7e2c6-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7e2c6-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7e2c6-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7e2c6-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7e2c6-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7e2c6-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7e2c6-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7e2c6-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="7e2c6-140">Método SetUILocale</span><span class="sxs-lookup"><span data-stu-id="7e2c6-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
