---
title: Método ICLRDomainManager::SetAppDomainManagerType
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea10f9b7d23d8ca6a94d05cac6e586b434c000d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435537"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="d299b-102">Método ICLRDomainManager::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="d299b-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="d299b-103">Especifica o tipo derivado de <xref:System.AppDomainManager?displayProperty=nameWithType> classe do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="d299b-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d299b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d299b-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d299b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d299b-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="d299b-106">[in] O nome para exibição do assembly que contém o tipo de Gerenciador de domínio de aplicativo; Por exemplo: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="d299b-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="d299b-107">[in] O nome do tipo de Gerenciador de domínio de aplicativo, incluindo o namespace.</span><span class="sxs-lookup"><span data-stu-id="d299b-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="d299b-108">[in] Uma combinação de [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) valores de enumeração que fornecem informações sobre o Gerenciador de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d299b-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d299b-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d299b-109">Return Value</span></span>  
 <span data-ttu-id="d299b-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="d299b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d299b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d299b-111">HRESULT</span></span>|<span data-ttu-id="d299b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d299b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d299b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d299b-113">S_OK</span></span>|<span data-ttu-id="d299b-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="d299b-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d299b-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d299b-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d299b-116">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d299b-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d299b-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d299b-117">Remarks</span></span>  
 <span data-ttu-id="d299b-118">No momento, o único valor definido para `dwInitializeDomainFlags` é `eInitializeNewDomainFlags_NoSecurityChanges`, que informa o common language runtime (CLR) que o Gerenciador de domínio de aplicativo não modificará as configurações de segurança durante a execução de <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="d299b-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d299b-119">Isso permite que o CLR otimizar o carregamento de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA).</span><span class="sxs-lookup"><span data-stu-id="d299b-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="d299b-120">Se o fechamento transitivo deste conjunto de módulos (assemblies) for grande, isso pode resultar em um aprimoramento significativo no tempo de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d299b-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d299b-121">Se o host especifica `eInitializeNewDomainFlags_NoSecurityChanges` para o Gerenciador de domínio de aplicativo, um <xref:System.InvalidOperationException> será lançada se qualquer tentativa de modificar a segurança do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d299b-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="d299b-122">Chamando o [: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)método é equivalente a chamar `ICLRDomainManager::SetAppDomainManagerType` com `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="d299b-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d299b-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d299b-123">Requirements</span></span>  
 <span data-ttu-id="d299b-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d299b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d299b-125">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d299b-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d299b-126">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d299b-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d299b-127">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d299b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d299b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d299b-128">See Also</span></span>  
 [<span data-ttu-id="d299b-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="d299b-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="d299b-130">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="d299b-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="d299b-131">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="d299b-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
