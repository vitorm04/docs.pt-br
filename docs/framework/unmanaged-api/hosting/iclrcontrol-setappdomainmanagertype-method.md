---
title: Método ICLRControl::SetAppDomainManagerType
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be778fed910b2cbdbf5e9ae7754abae437ef6bec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433728"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="a55b9-102">Método ICLRControl::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="a55b9-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="a55b9-103">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a55b9-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a55b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a55b9-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a55b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a55b9-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="a55b9-106">[in] O nome do assembly no qual o tipo solicitado derivado <xref:System.AppDomainManager> é implementado.</span><span class="sxs-lookup"><span data-stu-id="a55b9-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="a55b9-107">[in] O nome do tipo implementado no `pwzAppDomainManagerAssembly` parâmetro que implementa os recursos de <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="a55b9-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a55b9-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a55b9-108">Return Value</span></span>  
  
|<span data-ttu-id="a55b9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a55b9-109">HRESULT</span></span>|<span data-ttu-id="a55b9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a55b9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a55b9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a55b9-111">S_OK</span></span>|<span data-ttu-id="a55b9-112">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a55b9-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="a55b9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a55b9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a55b9-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a55b9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a55b9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a55b9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a55b9-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="a55b9-116">The call timed out.</span></span>|  
|<span data-ttu-id="a55b9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a55b9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a55b9-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a55b9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a55b9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a55b9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a55b9-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="a55b9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a55b9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a55b9-121">E_FAIL</span></span>|<span data-ttu-id="a55b9-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a55b9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a55b9-123">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a55b9-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a55b9-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a55b9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a55b9-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a55b9-125">Requirements</span></span>  
 <span data-ttu-id="a55b9-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a55b9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a55b9-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a55b9-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a55b9-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a55b9-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a55b9-129">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a55b9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55b9-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a55b9-130">See Also</span></span>  
 [<span data-ttu-id="a55b9-131">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="a55b9-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a55b9-132">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="a55b9-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
