---
title: "Método ICLRControl::SetAppDomainManagerType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6632417cb0cfe17d7bde16ecf47ae1c001f43f2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="fe66a-102">Método ICLRControl::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="fe66a-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="fe66a-103">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe66a-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe66a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe66a-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe66a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe66a-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="fe66a-106">[in] O nome do assembly no qual o tipo solicitado derivado <xref:System.AppDomainManager> é implementado.</span><span class="sxs-lookup"><span data-stu-id="fe66a-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="fe66a-107">[in] O nome do tipo implementado no `pwzAppDomainManagerAssembly` parâmetro que implementa os recursos de <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="fe66a-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe66a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fe66a-108">Return Value</span></span>  
  
|<span data-ttu-id="fe66a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe66a-109">HRESULT</span></span>|<span data-ttu-id="fe66a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe66a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe66a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe66a-111">S_OK</span></span>|<span data-ttu-id="fe66a-112">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="fe66a-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="fe66a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe66a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe66a-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="fe66a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe66a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe66a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe66a-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="fe66a-116">The call timed out.</span></span>|  
|<span data-ttu-id="fe66a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe66a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe66a-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="fe66a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe66a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe66a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe66a-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="fe66a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe66a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe66a-121">E_FAIL</span></span>|<span data-ttu-id="fe66a-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="fe66a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe66a-123">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="fe66a-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe66a-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fe66a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe66a-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe66a-125">Requirements</span></span>  
 <span data-ttu-id="fe66a-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe66a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe66a-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe66a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe66a-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fe66a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe66a-129">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe66a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe66a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe66a-130">See Also</span></span>  
 [<span data-ttu-id="fe66a-131">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="fe66a-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="fe66a-132">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="fe66a-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
