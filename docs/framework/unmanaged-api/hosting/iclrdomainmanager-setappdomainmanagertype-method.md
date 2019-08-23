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
ms.openlocfilehash: 9b142f1a05036eddf44c69d8b7da95091dc8f445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963089"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="91151-102">Método ICLRDomainManager::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="91151-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="91151-103">Especifica o tipo, derivado da <xref:System.AppDomainManager?displayProperty=nameWithType> classe, do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="91151-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91151-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91151-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91151-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91151-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="91151-106">no O nome de exibição do assembly que contém o tipo de Gerenciador de domínio do aplicativo; por exemplo: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="91151-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="91151-107">no O nome do tipo do Gerenciador de domínio do aplicativo, incluindo o namespace.</span><span class="sxs-lookup"><span data-stu-id="91151-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="91151-108">no Uma combinação de valores de enumeração [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) que fornecem informações sobre o Gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91151-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91151-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="91151-109">Return Value</span></span>  
 <span data-ttu-id="91151-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="91151-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="91151-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91151-111">HRESULT</span></span>|<span data-ttu-id="91151-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="91151-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91151-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="91151-113">S_OK</span></span>|<span data-ttu-id="91151-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="91151-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="91151-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91151-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91151-116">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="91151-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91151-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="91151-117">Remarks</span></span>  
 <span data-ttu-id="91151-118">Atualmente, o único valor definido para `dwInitializeDomainFlags` é `eInitializeNewDomainFlags_NoSecurityChanges`, que informa ao Common Language Runtime (CLR) que o Gerenciador de domínio do aplicativo não modificará as configurações de segurança <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> durante a execução do método.</span><span class="sxs-lookup"><span data-stu-id="91151-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="91151-119">Isso permite que o CLR Otimize o carregamento de assemblies que têm o atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> condicional (APTCA).</span><span class="sxs-lookup"><span data-stu-id="91151-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="91151-120">Isso pode resultar em uma melhoria significativa no tempo de inicialização se o fechamento transitivo desse conjunto de assemblies for grande.</span><span class="sxs-lookup"><span data-stu-id="91151-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="91151-121">Se o host especificar `eInitializeNewDomainFlags_NoSecurityChanges` o Gerenciador de domínio do aplicativo, <xref:System.InvalidOperationException> um será gerado se qualquer tentativa for feita para modificar a segurança do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91151-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="91151-122">Chamar o método [ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)é equivalente a chamar `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="91151-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91151-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91151-123">Requirements</span></span>  
 <span data-ttu-id="91151-124">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91151-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91151-125">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="91151-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="91151-126">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="91151-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91151-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91151-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91151-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91151-128">See also</span></span>

- [<span data-ttu-id="91151-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="91151-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="91151-130">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="91151-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="91151-131">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="91151-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
