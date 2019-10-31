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
ms.openlocfilehash: fa9608423456caeb6020e883a14f2c41583ac4d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126606"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="ea942-102">Método ICLRControl::GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="ea942-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="ea942-103">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador que o host pode usar para configurar o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ea942-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea942-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea942-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea942-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea942-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="ea942-106">no O `IID` do tipo de Gerenciador a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="ea942-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="ea942-107">Há suporte para os valores de `IID` a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea942-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="ea942-108">IID_ICLRDebugManager: Especifica que `ppObject` será do tipo [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ea942-109">IID_ICLRErrorReportingManager: Especifica que `ppObject` será do tipo [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ea942-110">IID_ICLRGCManager: Especifica que `ppObject` será do tipo [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ea942-111">IID_ICLRHostProtectionManager: Especifica que `ppObject` será do tipo [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ea942-112">IID_ICLROnEventManager: Especifica que `ppObject` será do tipo [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ea942-113">IID_ICLRPolicyManager: Especifica que `ppObject` será do tipo [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="ea942-114">IID_ICLRTaskManager: Especifica que `ppObject` será do tipo [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="ea942-115">fora Um ponteiro de interface para o Gerenciador solicitado, ou NULL, se um tipo de Gerenciador inválido foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="ea942-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea942-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ea942-116">Return Value</span></span>  
  
|<span data-ttu-id="ea942-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea942-117">HRESULT</span></span>|<span data-ttu-id="ea942-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea942-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea942-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea942-119">S_OK</span></span>|<span data-ttu-id="ea942-120">O método retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ea942-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="ea942-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea942-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea942-122">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ea942-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea942-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea942-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea942-124">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="ea942-124">The call timed out.</span></span>|  
|<span data-ttu-id="ea942-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea942-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea942-126">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ea942-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea942-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea942-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea942-128">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="ea942-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea942-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea942-129">E_FAIL</span></span>|<span data-ttu-id="ea942-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ea942-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea942-131">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="ea942-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea942-132">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea942-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ea942-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="ea942-133">E_NOINTERFACE</span></span>|<span data-ttu-id="ea942-134">Não há suporte para o tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="ea942-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea942-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea942-135">Requirements</span></span>  
 <span data-ttu-id="ea942-136">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea942-137">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ea942-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea942-138">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea942-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea942-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea942-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea942-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea942-140">See also</span></span>

- [<span data-ttu-id="ea942-141">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="ea942-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ea942-142">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="ea942-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
