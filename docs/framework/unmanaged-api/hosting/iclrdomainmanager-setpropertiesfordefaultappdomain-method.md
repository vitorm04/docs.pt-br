---
title: Método ICLRDomainManager::SetPropertiesForDefaultAppDomain
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f107847ddd48805f4779ff94c4e436a176688030
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699019"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="44242-102">Método ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="44242-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="44242-103">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="44242-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44242-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44242-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44242-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44242-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="44242-106">[in] O número de entradas no `pwszPropertyNames` e `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="44242-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="44242-107">[in] Uma matriz de nomes de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="44242-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="44242-108">Atualmente, o nome da propriedade única que é reconhecido por esse método é "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="44242-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="44242-109">[in] Uma matriz de valores de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="44242-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44242-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="44242-110">Return Value</span></span>  
 <span data-ttu-id="44242-111">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="44242-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44242-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44242-112">HRESULT</span></span>|<span data-ttu-id="44242-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="44242-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44242-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="44242-114">S_OK</span></span>|<span data-ttu-id="44242-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="44242-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="44242-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="44242-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="44242-117">`pwszPropertyNames` inclui um nome de propriedade que não é reconhecido por esse método.</span><span class="sxs-lookup"><span data-stu-id="44242-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44242-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="44242-118">Remarks</span></span>  
 <span data-ttu-id="44242-119">O valor da propriedade para "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" é uma lista de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) com o <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> sinalizador, que se tornarão visíveis para chamadores parcialmente confiáveis no aplicativo padrão domínio.</span><span class="sxs-lookup"><span data-stu-id="44242-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44242-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44242-120">Requirements</span></span>  
 <span data-ttu-id="44242-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44242-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44242-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="44242-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="44242-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="44242-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44242-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44242-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44242-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44242-125">See also</span></span>
- [<span data-ttu-id="44242-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="44242-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="44242-127">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="44242-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
