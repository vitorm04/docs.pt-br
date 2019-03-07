---
title: Método ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65ec26384b88ba3048666f3b6e3affcb90d8f070
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479305"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="be30d-102">Método ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="be30d-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="be30d-103">Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instância na lista fornecida de identidades de assembly parcial.</span><span class="sxs-lookup"><span data-stu-id="be30d-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be30d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be30d-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be30d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="be30d-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="be30d-106">[in] Uma matriz de cadeias de caracteres terminada em nulo no formulário "propriedade name = value..." que especificam uma lista de identidades de assembly parcial.</span><span class="sxs-lookup"><span data-stu-id="be30d-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="be30d-107">[in] O número de itens em `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="be30d-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="be30d-108">[out] Um ponteiro de interface para um `ICLRAssemblyReferenceList` objeto que contém os dados de identidade do assembly para a lista de assemblies especificados em `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="be30d-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be30d-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="be30d-109">Return Value</span></span>  
  
|<span data-ttu-id="be30d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be30d-110">HRESULT</span></span>|<span data-ttu-id="be30d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="be30d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be30d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="be30d-112">S_OK</span></span>|<span data-ttu-id="be30d-113">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="be30d-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="be30d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be30d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be30d-115">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="be30d-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="be30d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="be30d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="be30d-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="be30d-117">The call timed out.</span></span>|  
|<span data-ttu-id="be30d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="be30d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="be30d-119">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="be30d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="be30d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="be30d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="be30d-121">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="be30d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="be30d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be30d-122">E_FAIL</span></span>|<span data-ttu-id="be30d-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="be30d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="be30d-124">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="be30d-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="be30d-125">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="be30d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be30d-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be30d-126">Requirements</span></span>  
 <span data-ttu-id="be30d-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be30d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be30d-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="be30d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be30d-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="be30d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be30d-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be30d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be30d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be30d-131">See also</span></span>
- [<span data-ttu-id="be30d-132">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="be30d-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="be30d-133">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="be30d-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
