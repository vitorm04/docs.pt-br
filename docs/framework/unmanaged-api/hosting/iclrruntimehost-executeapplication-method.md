---
title: Método ICLRRuntimeHost::ExecuteApplication
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38938de335e5f0d7cb8051554c400f16df012362
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965350"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="7c466-102">Método ICLRRuntimeHost::ExecuteApplication</span><span class="sxs-lookup"><span data-stu-id="7c466-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="7c466-103">Usado em cenários de implantação ClickOnce baseados em manifesto para especificar o aplicativo a ser ativado em um novo domínio.</span><span class="sxs-lookup"><span data-stu-id="7c466-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="7c466-104">Para obter mais informações sobre esses cenários, consulte [segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="7c466-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c466-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c466-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c466-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c466-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="7c466-107">no O nome completo do aplicativo, conforme definido para <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="7c466-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="7c466-108">no O número de cadeias de caracteres `ppwzManifestPaths` contidas na matriz.</span><span class="sxs-lookup"><span data-stu-id="7c466-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="7c466-109">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="7c466-109">[in] Optional.</span></span> <span data-ttu-id="7c466-110">Uma matriz de cadeia de caracteres que contém caminhos de manifesto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c466-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="7c466-111">no O número de cadeias de caracteres `ppwzActivationData` contidas na matriz.</span><span class="sxs-lookup"><span data-stu-id="7c466-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="7c466-112">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="7c466-112">[in] Optional.</span></span> <span data-ttu-id="7c466-113">Uma matriz de cadeia de caracteres que contém os dados de ativação do aplicativo, como a parte da cadeia de caracteres de consulta da URL para aplicativos implantados na Web.</span><span class="sxs-lookup"><span data-stu-id="7c466-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="7c466-114">fora O valor retornado do ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c466-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c466-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7c466-115">Return Value</span></span>  
  
|<span data-ttu-id="7c466-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c466-116">HRESULT</span></span>|<span data-ttu-id="7c466-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c466-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c466-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c466-118">S_OK</span></span>|<span data-ttu-id="7c466-119">`ExecuteApplication`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7c466-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="7c466-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c466-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c466-121">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7c466-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c466-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c466-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c466-123">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7c466-123">The call timed out.</span></span>|  
|<span data-ttu-id="7c466-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c466-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c466-125">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7c466-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c466-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c466-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c466-127">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="7c466-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c466-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c466-128">E_FAIL</span></span>|<span data-ttu-id="7c466-129">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7c466-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c466-130">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="7c466-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c466-131">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7c466-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c466-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c466-132">Remarks</span></span>  
 <span data-ttu-id="7c466-133">`ExecuteApplication`é usado para ativar aplicativos ClickOnce em um domínio de aplicativo recém-criado.</span><span class="sxs-lookup"><span data-stu-id="7c466-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="7c466-134">O `pReturnValue` parâmetro de saída é definido como o valor retornado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c466-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="7c466-135">Se você fornecer um valor de NULL para `pReturnValue`, `ExecuteApplication` o não falhará, mas não retornará um valor.</span><span class="sxs-lookup"><span data-stu-id="7c466-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7c466-136">Não chame o método [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) antes de chamar o `ExecuteApplication` método para ativar um aplicativo baseado em manifesto.</span><span class="sxs-lookup"><span data-stu-id="7c466-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="7c466-137">Se o `Start` método for chamado primeiro, a `ExecuteApplication` chamada do método falhará.</span><span class="sxs-lookup"><span data-stu-id="7c466-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c466-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c466-138">Requirements</span></span>  
 <span data-ttu-id="7c466-139">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c466-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c466-140">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c466-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c466-141">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c466-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c466-142">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c466-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c466-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c466-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="7c466-144">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="7c466-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="7c466-145">Método SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="7c466-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="7c466-146">Passo a passo: Como baixar assemblies sob demanda com a API de implantação do ClickOnce usando o designer</span><span class="sxs-lookup"><span data-stu-id="7c466-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
