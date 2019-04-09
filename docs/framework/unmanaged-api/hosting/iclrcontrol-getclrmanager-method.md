---
title: Método ICLRControl::GetCLRManager
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33c790bf2721f09b263494e845356ef6b6712f99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177132"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="23fff-102">Método ICLRControl::GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="23fff-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="23fff-103">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador que o host pode usar para configurar o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="23fff-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23fff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23fff-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23fff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23fff-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="23fff-106">[in] O `IID` do tipo de Gerenciador para retornar.</span><span class="sxs-lookup"><span data-stu-id="23fff-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="23fff-107">O seguinte `IID` valores têm suporte.</span><span class="sxs-lookup"><span data-stu-id="23fff-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="23fff-108">IID_ICLRDebugManager: Especifica que `ppObject` será do tipo [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23fff-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="23fff-109">IID_ICLRErrorReportingManager: Especifica que `ppObject` será do tipo [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23fff-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="23fff-110">IID_ICLRGCManager: Especifica que `ppObject` será do tipo [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23fff-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="23fff-111">IID_ICLRHostProtectionManager: Especifica que `ppObject` será do tipo [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23fff-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="23fff-112">IID_ICLROnEventManager: Especifica que `ppObject` será do tipo [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23fff-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="23fff-113">IID_ICLRPolicyManager: Especifica que `ppObject` será do tipo [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23fff-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="23fff-114">IID_ICLRTaskManager: speciries que `ppObject` será do tipo [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23fff-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="23fff-115">[out] Um ponteiro de interface para o Gerenciador solicitado ou null, se um tipo de Gerenciador inválido foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="23fff-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23fff-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="23fff-116">Return Value</span></span>  
  
|<span data-ttu-id="23fff-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23fff-117">HRESULT</span></span>|<span data-ttu-id="23fff-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="23fff-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23fff-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="23fff-119">S_OK</span></span>|<span data-ttu-id="23fff-120">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="23fff-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="23fff-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23fff-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23fff-122">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="23fff-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="23fff-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="23fff-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="23fff-124">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="23fff-124">The call timed out.</span></span>|  
|<span data-ttu-id="23fff-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="23fff-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="23fff-126">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="23fff-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="23fff-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="23fff-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="23fff-128">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="23fff-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="23fff-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23fff-129">E_FAIL</span></span>|<span data-ttu-id="23fff-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="23fff-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="23fff-131">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="23fff-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="23fff-132">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="23fff-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="23fff-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="23fff-133">E_NOINTERFACE</span></span>|<span data-ttu-id="23fff-134">Não há suporte para o tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="23fff-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23fff-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23fff-135">Requirements</span></span>  
 <span data-ttu-id="23fff-136">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23fff-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23fff-137">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="23fff-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23fff-138">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="23fff-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="23fff-139">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="23fff-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="23fff-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23fff-140">See also</span></span>

- [<span data-ttu-id="23fff-141">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="23fff-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="23fff-142">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="23fff-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
