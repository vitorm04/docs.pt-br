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
ms.openlocfilehash: 18db77b42af47b76bf1b3b66748d586c4c41dbd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433548"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="ca16d-102">Método ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="ca16d-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="ca16d-103">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="ca16d-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca16d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca16d-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca16d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca16d-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="ca16d-106">[in] O número de entradas em `pwszPropertyNames` e `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="ca16d-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="ca16d-107">[in] Uma matriz de nomes de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="ca16d-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="ca16d-108">Atualmente, o nome de propriedade só é reconhecido por este método é "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="ca16d-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="ca16d-109">[in] Uma matriz de valores de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="ca16d-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca16d-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ca16d-110">Return Value</span></span>  
 <span data-ttu-id="ca16d-111">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="ca16d-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ca16d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca16d-112">HRESULT</span></span>|<span data-ttu-id="ca16d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca16d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca16d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca16d-114">S_OK</span></span>|<span data-ttu-id="ca16d-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="ca16d-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="ca16d-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="ca16d-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="ca16d-117">`pwszPropertyNames` inclui um nome de propriedade que não é reconhecido por este método.</span><span class="sxs-lookup"><span data-stu-id="ca16d-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca16d-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca16d-118">Remarks</span></span>  
 <span data-ttu-id="ca16d-119">O valor da propriedade para "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" é uma lista de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) com o <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> sinalizador, que devem ficar visíveis para chamadores parcialmente confiáveis no aplicativo padrão domínio.</span><span class="sxs-lookup"><span data-stu-id="ca16d-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca16d-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca16d-120">Requirements</span></span>  
 <span data-ttu-id="ca16d-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca16d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca16d-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ca16d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ca16d-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ca16d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca16d-124">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca16d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca16d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca16d-125">See Also</span></span>  
 [<span data-ttu-id="ca16d-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="ca16d-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="ca16d-127">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="ca16d-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
