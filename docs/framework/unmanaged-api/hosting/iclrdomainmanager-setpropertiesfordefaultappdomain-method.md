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
ms.openlocfilehash: cd725f7468b26f9d8af3d7928b9df6fbefd93b6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502495"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="bacd4-102">Método ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="bacd4-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="bacd4-103">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="bacd4-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bacd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bacd4-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bacd4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bacd4-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="bacd4-106">[in] O número de entradas no `pwszPropertyNames` e `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="bacd4-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="bacd4-107">[in] Uma matriz de nomes de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="bacd4-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="bacd4-108">Atualmente, o nome da propriedade única que é reconhecido por esse método é "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="bacd4-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="bacd4-109">[in] Uma matriz de valores de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="bacd4-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bacd4-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bacd4-110">Return Value</span></span>  
 <span data-ttu-id="bacd4-111">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="bacd4-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bacd4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bacd4-112">HRESULT</span></span>|<span data-ttu-id="bacd4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bacd4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bacd4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bacd4-114">S_OK</span></span>|<span data-ttu-id="bacd4-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="bacd4-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="bacd4-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="bacd4-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="bacd4-117">`pwszPropertyNames` inclui um nome de propriedade que não é reconhecido por esse método.</span><span class="sxs-lookup"><span data-stu-id="bacd4-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bacd4-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="bacd4-118">Remarks</span></span>  
 <span data-ttu-id="bacd4-119">O valor da propriedade para "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" é uma lista de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) com o <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> sinalizador, que se tornarão visíveis para chamadores parcialmente confiáveis no aplicativo padrão domínio.</span><span class="sxs-lookup"><span data-stu-id="bacd4-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bacd4-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bacd4-120">Requirements</span></span>  
 <span data-ttu-id="bacd4-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bacd4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bacd4-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bacd4-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bacd4-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bacd4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bacd4-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bacd4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bacd4-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bacd4-125">See also</span></span>
- [<span data-ttu-id="bacd4-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="bacd4-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="bacd4-127">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="bacd4-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
