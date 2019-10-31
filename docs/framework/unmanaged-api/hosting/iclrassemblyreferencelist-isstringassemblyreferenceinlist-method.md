---
title: Método ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
ms.openlocfilehash: 4dc91723f009d46f9c57b1c99aa66ba7a1b127e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126640"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="1af80-102">Método ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="1af80-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="1af80-103">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="1af80-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1af80-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1af80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1af80-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="1af80-106">no O nome do assembly para o qual Pesquisar.</span><span class="sxs-lookup"><span data-stu-id="1af80-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1af80-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1af80-107">Return Value</span></span>  
  
|<span data-ttu-id="1af80-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1af80-108">HRESULT</span></span>|<span data-ttu-id="1af80-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1af80-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1af80-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1af80-110">S_OK</span></span>|<span data-ttu-id="1af80-111">A cadeia de caracteres aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="1af80-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="1af80-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1af80-112">S_FALSE</span></span>|<span data-ttu-id="1af80-113">A cadeia de caracteres não aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="1af80-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="1af80-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1af80-114">E_FAIL</span></span>|<span data-ttu-id="1af80-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1af80-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1af80-116">Depois que um método retorna E_FAIL, o Common Language Runtime não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="1af80-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="1af80-117">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1af80-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1af80-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1af80-118">Requirements</span></span>  
 <span data-ttu-id="1af80-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1af80-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1af80-120">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1af80-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1af80-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1af80-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1af80-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1af80-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af80-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1af80-123">See also</span></span>

- [<span data-ttu-id="1af80-124">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="1af80-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="1af80-125">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="1af80-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1af80-126">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="1af80-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="1af80-127">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="1af80-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
