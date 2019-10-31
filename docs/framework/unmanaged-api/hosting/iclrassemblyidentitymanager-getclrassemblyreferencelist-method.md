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
ms.openlocfilehash: 54c11e78438ae97e1fc0c715c9161361784b3be6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126728"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="80aa7-102">Método ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="80aa7-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="80aa7-103">Obtém um ponteiro de interface para uma instância de [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) da lista fornecida de identidades de assembly parciais.</span><span class="sxs-lookup"><span data-stu-id="80aa7-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80aa7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80aa7-104">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80aa7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80aa7-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="80aa7-106">no Uma matriz de cadeias de caracteres terminadas em nulo no formato "nome, propriedade = valor..." Isso especifica uma lista de identidades de assembly parciais.</span><span class="sxs-lookup"><span data-stu-id="80aa7-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="80aa7-107">no O número de itens em `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="80aa7-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="80aa7-108">fora Um ponteiro de interface para um objeto `ICLRAssemblyReferenceList` que contém os dados de identidade do assembly para a lista de assemblies especificados em `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="80aa7-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80aa7-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="80aa7-109">Return Value</span></span>  
  
|<span data-ttu-id="80aa7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80aa7-110">HRESULT</span></span>|<span data-ttu-id="80aa7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="80aa7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80aa7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="80aa7-112">S_OK</span></span>|<span data-ttu-id="80aa7-113">O método retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="80aa7-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="80aa7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80aa7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80aa7-115">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="80aa7-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80aa7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80aa7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80aa7-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="80aa7-117">The call timed out.</span></span>|  
|<span data-ttu-id="80aa7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80aa7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80aa7-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="80aa7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80aa7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80aa7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80aa7-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="80aa7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80aa7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80aa7-122">E_FAIL</span></span>|<span data-ttu-id="80aa7-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="80aa7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80aa7-124">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="80aa7-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80aa7-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="80aa7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80aa7-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80aa7-126">Requirements</span></span>  
 <span data-ttu-id="80aa7-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80aa7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80aa7-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80aa7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80aa7-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80aa7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80aa7-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80aa7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80aa7-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80aa7-131">See also</span></span>

- [<span data-ttu-id="80aa7-132">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="80aa7-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="80aa7-133">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="80aa7-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
