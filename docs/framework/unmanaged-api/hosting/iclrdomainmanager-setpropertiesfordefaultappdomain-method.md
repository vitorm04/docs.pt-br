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
ms.openlocfilehash: 4c42297e848844617ffdc6c85c81846b5805eb4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181318"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="a7431-102">Método ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="a7431-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="a7431-103">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="a7431-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7431-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7431-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7431-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7431-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="a7431-106">[in] O número de entradas no `pwszPropertyNames` e `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="a7431-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="a7431-107">[in] Uma matriz de nomes de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="a7431-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="a7431-108">Atualmente, o nome da propriedade única que é reconhecido por esse método é "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="a7431-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="a7431-109">[in] Uma matriz de valores de propriedade, ou nulo se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="a7431-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7431-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a7431-110">Return Value</span></span>  
 <span data-ttu-id="a7431-111">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="a7431-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a7431-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7431-112">HRESULT</span></span>|<span data-ttu-id="a7431-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7431-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7431-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7431-114">S_OK</span></span>|<span data-ttu-id="a7431-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a7431-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="a7431-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="a7431-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|`pwszPropertyNames` <span data-ttu-id="a7431-117">inclui um nome de propriedade que não é reconhecido por esse método.</span><span class="sxs-lookup"><span data-stu-id="a7431-117">includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7431-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7431-118">Remarks</span></span>  
 <span data-ttu-id="a7431-119">O valor da propriedade para "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" é uma lista de assemblies que têm a condicional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) com o <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> sinalizador, que se tornarão visíveis para chamadores parcialmente confiáveis no aplicativo padrão domínio.</span><span class="sxs-lookup"><span data-stu-id="a7431-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7431-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7431-120">Requirements</span></span>  
 <span data-ttu-id="a7431-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7431-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7431-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a7431-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a7431-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a7431-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a7431-124">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a7431-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a7431-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7431-125">See also</span></span>

- [<span data-ttu-id="a7431-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a7431-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="a7431-127">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="a7431-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
