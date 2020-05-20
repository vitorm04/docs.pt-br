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
ms.openlocfilehash: 5e1c1b1984c63bedb3c073f45a7b9a3574afdcec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615677"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="850bd-102">Método ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="850bd-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="850bd-103">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="850bd-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="850bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="850bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="850bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="850bd-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="850bd-106">no O número de entradas no `pwszPropertyNames` e no `pwszPropertyValues` .</span><span class="sxs-lookup"><span data-stu-id="850bd-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="850bd-107">no Uma matriz de nomes de propriedade ou NULL se não houver propriedades.</span><span class="sxs-lookup"><span data-stu-id="850bd-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="850bd-108">Atualmente, o único nome de propriedade reconhecido por esse método é "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="850bd-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="850bd-109">no Uma matriz de valores de propriedade ou NULL se não houver nenhuma propriedade.</span><span class="sxs-lookup"><span data-stu-id="850bd-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="850bd-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="850bd-110">Return Value</span></span>  
 <span data-ttu-id="850bd-111">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="850bd-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="850bd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="850bd-112">HRESULT</span></span>|<span data-ttu-id="850bd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="850bd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="850bd-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="850bd-114">S_OK</span></span>|<span data-ttu-id="850bd-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="850bd-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="850bd-116">HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="850bd-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="850bd-117">`pwszPropertyNames`inclui um nome de propriedade que não é reconhecido por este método.</span><span class="sxs-lookup"><span data-stu-id="850bd-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="850bd-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="850bd-118">Remarks</span></span>  
 <span data-ttu-id="850bd-119">O valor da propriedade para "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" é uma lista de ASSEMBLIES que têm o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo condicional (APTCA) com o <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> sinalizador, que deve se tornar visível para chamadores parcialmente confiáveis no domínio do aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="850bd-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="850bd-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="850bd-120">Requirements</span></span>  
 <span data-ttu-id="850bd-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="850bd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="850bd-122">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="850bd-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="850bd-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="850bd-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="850bd-124">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="850bd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850bd-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="850bd-125">See also</span></span>

- [<span data-ttu-id="850bd-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="850bd-126">Hosting</span></span>](index.md)
- [<span data-ttu-id="850bd-127">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="850bd-127">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
