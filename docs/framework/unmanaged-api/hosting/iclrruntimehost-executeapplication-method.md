---
title: "Método ICLRRuntimeHost::ExecuteApplication"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteApplication
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3b43365ad208dae5b28b31cf494de37ca670d791
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="189b2-102">Método ICLRRuntimeHost::ExecuteApplication</span><span class="sxs-lookup"><span data-stu-id="189b2-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="189b2-103">Usado em cenários de implantação de ClickOnce baseado no manifesto para especificar o aplicativo a ser ativado em um novo domínio.</span><span class="sxs-lookup"><span data-stu-id="189b2-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="189b2-104">Para obter mais informações sobre esses cenários, consulte [segurança ClickOnce e implantação](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="189b2-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="189b2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="189b2-105">Syntax</span></span>  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="189b2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="189b2-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="189b2-107">[in] O nome completo do aplicativo, conforme definido para <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="189b2-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="189b2-108">[in] O número de cadeias de caracteres dentro de `ppwzManifestPaths` matriz.</span><span class="sxs-lookup"><span data-stu-id="189b2-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="189b2-109">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="189b2-109">[in] Optional.</span></span> <span data-ttu-id="189b2-110">Uma matriz de cadeia de caracteres que contém os caminhos do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="189b2-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="189b2-111">[in] O número de cadeias de caracteres dentro de `ppwzActivationData` matriz.</span><span class="sxs-lookup"><span data-stu-id="189b2-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="189b2-112">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="189b2-112">[in] Optional.</span></span> <span data-ttu-id="189b2-113">Uma matriz de cadeia de caracteres que contém os dados de ativação do aplicativo, como a parte da cadeia de caracteres de consulta da URL para os aplicativos implantados pela Web.</span><span class="sxs-lookup"><span data-stu-id="189b2-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="189b2-114">[out] O valor retornado do ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="189b2-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="189b2-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="189b2-115">Return Value</span></span>  
  
|<span data-ttu-id="189b2-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="189b2-116">HRESULT</span></span>|<span data-ttu-id="189b2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="189b2-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="189b2-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="189b2-118">S_OK</span></span>|<span data-ttu-id="189b2-119">`ExecuteApplication`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="189b2-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="189b2-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="189b2-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="189b2-121">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="189b2-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="189b2-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="189b2-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="189b2-123">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="189b2-123">The call timed out.</span></span>|  
|<span data-ttu-id="189b2-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="189b2-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="189b2-125">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="189b2-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="189b2-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="189b2-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="189b2-127">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="189b2-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="189b2-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="189b2-128">E_FAIL</span></span>|<span data-ttu-id="189b2-129">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="189b2-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="189b2-130">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="189b2-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="189b2-131">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="189b2-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="189b2-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="189b2-132">Remarks</span></span>  
 <span data-ttu-id="189b2-133">`ExecuteApplication`é usada para ativar aplicativos ClickOnce em um domínio de aplicativo recém-criado.</span><span class="sxs-lookup"><span data-stu-id="189b2-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="189b2-134">O `pReturnValue` parâmetro de saída é definido como o valor retornado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="189b2-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="189b2-135">Se você fornecer um valor nulo para `pReturnValue`, `ExecuteApplication` não falha, mas não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="189b2-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="189b2-136">Não chame o [método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método antes de chamar o `ExecuteApplication` método para ativar um aplicativo baseado no manifesto.</span><span class="sxs-lookup"><span data-stu-id="189b2-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="189b2-137">Se o `Start` método é chamado pela primeira vez, o `ExecuteApplication` haverá falha na chamada de método.</span><span class="sxs-lookup"><span data-stu-id="189b2-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="189b2-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="189b2-138">Requirements</span></span>  
 <span data-ttu-id="189b2-139">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="189b2-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="189b2-140">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="189b2-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="189b2-141">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="189b2-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="189b2-142">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="189b2-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="189b2-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="189b2-143">See Also</span></span>  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [<span data-ttu-id="189b2-144">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="189b2-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="189b2-145">Método SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="189b2-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [<span data-ttu-id="189b2-146">Passo a passo: baixando assemblies sob demanda com a API de implantação do ClickOnce usando o designer</span><span class="sxs-lookup"><span data-stu-id="189b2-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
