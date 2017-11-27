---
title: "Método ICLRControl::GetCLRManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.GetCLRManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3dc6f707511f9d6f4883aecbd2a26a587a902c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="7de26-102">Método ICLRControl::GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="7de26-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="7de26-103">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador, que o host pode usar para configurar o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7de26-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7de26-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7de26-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7de26-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7de26-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="7de26-106">[in] O `IID` do tipo de Gerenciador para retornar.</span><span class="sxs-lookup"><span data-stu-id="7de26-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="7de26-107">O seguinte `IID` valores têm suporte.</span><span class="sxs-lookup"><span data-stu-id="7de26-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="7de26-108">IID_ICLRDebugManager: Especifica que `ppObject` será do tipo [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7de26-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7de26-109">IID_ICLRErrorReportingManager: Especifica que `ppObject` será do tipo [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7de26-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7de26-110">IID_ICLRGCManager: Especifica que `ppObject` será do tipo [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7de26-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7de26-111">IID_ICLRHostProtectionManager: Especifica que `ppObject` será do tipo [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7de26-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7de26-112">IID_ICLROnEventManager: Especifica que `ppObject` será do tipo [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7de26-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7de26-113">IID_ICLRPolicyManager: Especifica que `ppObject` será do tipo [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7de26-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7de26-114">IID_ICLRTaskManager: speciries que `ppObject` será do tipo [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7de26-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="7de26-115">[out] Um ponteiro de interface para o Gerenciador solicitado, ou nulo, se um tipo de Gerenciador inválida foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="7de26-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7de26-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7de26-116">Return Value</span></span>  
  
|<span data-ttu-id="7de26-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7de26-117">HRESULT</span></span>|<span data-ttu-id="7de26-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7de26-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7de26-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="7de26-119">S_OK</span></span>|<span data-ttu-id="7de26-120">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7de26-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="7de26-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7de26-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7de26-122">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7de26-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7de26-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7de26-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7de26-124">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="7de26-124">The call timed out.</span></span>|  
|<span data-ttu-id="7de26-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7de26-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7de26-126">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7de26-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7de26-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7de26-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7de26-128">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="7de26-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7de26-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7de26-129">E_FAIL</span></span>|<span data-ttu-id="7de26-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7de26-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7de26-131">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7de26-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7de26-132">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7de26-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7de26-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="7de26-133">E_NOINTERFACE</span></span>|<span data-ttu-id="7de26-134">Não há suporte para o tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="7de26-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7de26-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7de26-135">Requirements</span></span>  
 <span data-ttu-id="7de26-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7de26-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7de26-137">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7de26-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7de26-138">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7de26-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7de26-139">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7de26-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de26-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7de26-140">See Also</span></span>  
 [<span data-ttu-id="7de26-141">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="7de26-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="7de26-142">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="7de26-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
