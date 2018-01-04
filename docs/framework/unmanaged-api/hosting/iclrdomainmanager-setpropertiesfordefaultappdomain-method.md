---
title: "Método ICLRDomainManager::SetPropertiesForDefaultAppDomain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de72568f5908dc89c9a4105c927cfba6c7366b80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="09c3c-102">Método ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="09c3c-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="09c3c-103">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="09c3c-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09c3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09c3c-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09c3c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="09c3c-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="09c3c-106">[in] O número de entradas em `pwszPropertyNames` e `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="09c3c-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="09c3c-107">[in] Uma matriz de nomes de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="09c3c-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="09c3c-108">Atualmente, o nome de propriedade só é reconhecido por este método é "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="09c3c-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="09c3c-109">[in] Uma matriz de valores de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="09c3c-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09c3c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="09c3c-110">Return Value</span></span>  
 <span data-ttu-id="09c3c-111">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="09c3c-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="09c3c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09c3c-112">HRESULT</span></span>|<span data-ttu-id="09c3c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="09c3c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09c3c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="09c3c-114">S_OK</span></span>|<span data-ttu-id="09c3c-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="09c3c-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="09c3c-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="09c3c-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="09c3c-117">`pwszPropertyNames`inclui um nome de propriedade que não é reconhecido por este método.</span><span class="sxs-lookup"><span data-stu-id="09c3c-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09c3c-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="09c3c-118">Remarks</span></span>  
 <span data-ttu-id="09c3c-119">O valor da propriedade para "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" é uma lista de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) com o <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> sinalizador, que devem ficar visíveis para chamadores parcialmente confiáveis no aplicativo padrão domínio.</span><span class="sxs-lookup"><span data-stu-id="09c3c-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09c3c-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09c3c-120">Requirements</span></span>  
 <span data-ttu-id="09c3c-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09c3c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09c3c-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="09c3c-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="09c3c-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="09c3c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09c3c-124">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09c3c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c3c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09c3c-125">See Also</span></span>  
 [<span data-ttu-id="09c3c-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="09c3c-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="09c3c-127">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="09c3c-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
