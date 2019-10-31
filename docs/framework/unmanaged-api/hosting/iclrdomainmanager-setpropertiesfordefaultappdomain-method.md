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
ms.openlocfilehash: 37919be2d0ebd7d243615bc5845b0781ac13e574
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129309"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="89131-102">Método ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="89131-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="89131-103">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="89131-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89131-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89131-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89131-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89131-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="89131-106">no O número de entradas em `pwszPropertyNames` e `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="89131-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="89131-107">no Uma matriz de nomes de propriedade ou NULL se não houver propriedades.</span><span class="sxs-lookup"><span data-stu-id="89131-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="89131-108">Atualmente, o único nome de propriedade reconhecido por esse método é "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="89131-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="89131-109">no Uma matriz de valores de propriedade ou NULL se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="89131-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89131-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="89131-110">Return Value</span></span>  
 <span data-ttu-id="89131-111">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="89131-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89131-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89131-112">HRESULT</span></span>|<span data-ttu-id="89131-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="89131-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89131-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="89131-114">S_OK</span></span>|<span data-ttu-id="89131-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="89131-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="89131-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="89131-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="89131-117">`pwszPropertyNames` inclui um nome de propriedade que não é reconhecido por esse método.</span><span class="sxs-lookup"><span data-stu-id="89131-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89131-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="89131-118">Remarks</span></span>  
 <span data-ttu-id="89131-119">O valor da propriedade para "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" é uma lista de ASSEMBLIES que têm o atributo APTCA (<xref:System.Security.AllowPartiallyTrustedCallersAttribute> condicional) com o sinalizador <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType>, que devem ser visíveis para chamadores parcialmente confiáveis no domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="89131-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89131-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89131-120">Requirements</span></span>  
 <span data-ttu-id="89131-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89131-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89131-122">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="89131-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="89131-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89131-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89131-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89131-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89131-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89131-125">See also</span></span>

- [<span data-ttu-id="89131-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="89131-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="89131-127">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="89131-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
