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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e544d251d7a1140e8604dcf27e049e49f91541fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708552"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="63f71-102">Método ICLRTaskManager::SetUILocale</span><span class="sxs-lookup"><span data-stu-id="63f71-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="63f71-103">Notifica o common language runtime (CLR) que o host tenha modificado a localidade do usuário (UI) de interface ou cultura, a tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="63f71-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63f71-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63f71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="63f71-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="63f71-106">[in] O valor do identificador de localidade que é mapeado para a cultura geográfica recentemente atribuída e o idioma da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="63f71-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63f71-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="63f71-107">Return Value</span></span>  
  
|<span data-ttu-id="63f71-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63f71-108">HRESULT</span></span>|<span data-ttu-id="63f71-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="63f71-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63f71-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="63f71-110">S_OK</span></span>|<span data-ttu-id="63f71-111">`SetUILocale` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="63f71-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="63f71-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="63f71-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="63f71-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="63f71-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="63f71-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="63f71-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="63f71-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="63f71-115">The call timed out.</span></span>|  
|<span data-ttu-id="63f71-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="63f71-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="63f71-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="63f71-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="63f71-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="63f71-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="63f71-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="63f71-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="63f71-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="63f71-120">E_FAIL</span></span>|<span data-ttu-id="63f71-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="63f71-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="63f71-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="63f71-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="63f71-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="63f71-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63f71-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="63f71-124">Remarks</span></span>  
 <span data-ttu-id="63f71-125">`SetUILocale` Fornece uma oportunidade para o host executar os mecanismos que ele pode ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="63f71-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f71-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63f71-126">Requirements</span></span>  
 <span data-ttu-id="63f71-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63f71-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63f71-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63f71-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63f71-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="63f71-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63f71-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63f71-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f71-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63f71-131">See also</span></span>
- [<span data-ttu-id="63f71-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="63f71-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="63f71-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="63f71-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="63f71-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="63f71-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="63f71-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="63f71-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
