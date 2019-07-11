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
ms.openlocfilehash: 28feddffff7dc5dba1860b3d2d1327a17bd08190
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772943"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="d8735-102">Método ICLRDomainManager::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="d8735-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="d8735-103">Especifica o tipo, derivado de <xref:System.AppDomainManager?displayProperty=nameWithType> classe do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="d8735-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8735-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8735-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8735-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8735-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="d8735-106">[in] O nome de exibição do assembly que contém o tipo de Gerenciador de domínio de aplicativo; Por exemplo: "AdMgrExample, versão Version=1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="d8735-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="d8735-107">[in] O nome do tipo de Gerenciador de domínio, incluindo o namespace.</span><span class="sxs-lookup"><span data-stu-id="d8735-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="d8735-108">[in] Uma combinação de [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) valores de enumeração que fornecem informações sobre o Gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8735-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8735-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8735-109">Return Value</span></span>  
 <span data-ttu-id="d8735-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="d8735-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d8735-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8735-111">HRESULT</span></span>|<span data-ttu-id="d8735-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8735-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8735-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8735-113">S_OK</span></span>|<span data-ttu-id="d8735-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="d8735-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d8735-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8735-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8735-116">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d8735-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8735-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8735-117">Remarks</span></span>  
 <span data-ttu-id="d8735-118">Atualmente, o único valor definido para `dwInitializeDomainFlags` está `eInitializeNewDomainFlags_NoSecurityChanges`, que informa o common language runtime (CLR) que o Gerenciador de domínio de aplicativo não modificará as configurações de segurança durante a execução do <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="d8735-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d8735-119">Isso permite que o CLR otimizar o carregamento de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA).</span><span class="sxs-lookup"><span data-stu-id="d8735-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="d8735-120">Isso pode resultar em uma melhoria significativa no tempo de inicialização se o fechamento transitivo desse conjunto de módulos (assemblies) for grande.</span><span class="sxs-lookup"><span data-stu-id="d8735-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d8735-121">Se o host especifica `eInitializeNewDomainFlags_NoSecurityChanges` para o Gerenciador de domínio de aplicativo, um <xref:System.InvalidOperationException> será lançada se qualquer tentativa de modificar a segurança do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8735-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="d8735-122">Chamar o [iclrcontrol:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)método é equivalente a chamar `ICLRDomainManager::SetAppDomainManagerType` com `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="d8735-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8735-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8735-123">Requirements</span></span>  
 <span data-ttu-id="d8735-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8735-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8735-125">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d8735-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d8735-126">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d8735-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8735-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8735-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8735-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8735-128">See also</span></span>

- [<span data-ttu-id="d8735-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="d8735-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="d8735-130">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="d8735-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="d8735-131">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="d8735-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
