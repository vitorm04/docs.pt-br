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
ms.openlocfilehash: 89b3f9f248a445cc0568236d6a1df14269de4187
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615690"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="06451-102">Método ICLRDomainManager::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="06451-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="06451-103">Especifica o tipo, derivado da <xref:System.AppDomainManager?displayProperty=nameWithType> classe, do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="06451-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06451-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06451-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06451-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06451-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="06451-106">no O nome de exibição do assembly que contém o tipo de Gerenciador de domínio do aplicativo; por exemplo: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".</span><span class="sxs-lookup"><span data-stu-id="06451-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="06451-107">no O nome do tipo do Gerenciador de domínio do aplicativo, incluindo o namespace.</span><span class="sxs-lookup"><span data-stu-id="06451-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="06451-108">no Uma combinação de valores de enumeração [EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md) que fornecem informações sobre o Gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06451-108">[in] A combination of [EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06451-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="06451-109">Return Value</span></span>  
 <span data-ttu-id="06451-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="06451-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="06451-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06451-111">HRESULT</span></span>|<span data-ttu-id="06451-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="06451-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06451-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="06451-113">S_OK</span></span>|<span data-ttu-id="06451-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="06451-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="06451-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="06451-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="06451-116">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="06451-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06451-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="06451-117">Remarks</span></span>  
 <span data-ttu-id="06451-118">Atualmente, o único valor definido para `dwInitializeDomainFlags` é `eInitializeNewDomainFlags_NoSecurityChanges` , que informa ao Common Language Runtime (CLR) que o Gerenciador de domínio do aplicativo não modificará as configurações de segurança durante a execução do <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="06451-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="06451-119">Isso permite que o CLR Otimize o carregamento de assemblies que têm o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo condicional (APTCA).</span><span class="sxs-lookup"><span data-stu-id="06451-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="06451-120">Isso pode resultar em uma melhoria significativa no tempo de inicialização se o fechamento transitivo desse conjunto de assemblies for grande.</span><span class="sxs-lookup"><span data-stu-id="06451-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="06451-121">Se o host especificar o `eInitializeNewDomainFlags_NoSecurityChanges` Gerenciador de domínio do aplicativo, um <xref:System.InvalidOperationException> será gerado se qualquer tentativa for feita para modificar a segurança do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06451-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="06451-122">Chamar o método [ICLRControl:: SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)é equivalente a chamar `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None` .</span><span class="sxs-lookup"><span data-stu-id="06451-122">Calling the [ICLRControl::SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06451-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06451-123">Requirements</span></span>  
 <span data-ttu-id="06451-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06451-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06451-125">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="06451-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="06451-126">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="06451-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06451-127">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06451-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06451-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="06451-128">See also</span></span>

- [<span data-ttu-id="06451-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="06451-129">Hosting</span></span>](index.md)
- [<span data-ttu-id="06451-130">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="06451-130">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
- [<span data-ttu-id="06451-131">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="06451-131">EInitializeNewDomainFlags Enumeration</span></span>](einitializenewdomainflags-enumeration.md)
