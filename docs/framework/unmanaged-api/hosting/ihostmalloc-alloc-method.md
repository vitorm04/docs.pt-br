---
title: Método IHostMAlloc::Alloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32499e74e8af9a865347bd800d3db4c303a7344c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126380"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="bf864-102">Método IHostMAlloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="bf864-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="bf864-103">Solicita que o host alocar a quantidade especificada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="bf864-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf864-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf864-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf864-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf864-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="bf864-106">[in] O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="bf864-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="bf864-107">[in] Um dos [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valores, que indica o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="bf864-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="bf864-108">[out] Um ponteiro para a memória alocada, ou nulo se a solicitação não pôde ser concluída.</span><span class="sxs-lookup"><span data-stu-id="bf864-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf864-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bf864-109">Return Value</span></span>  
  
|<span data-ttu-id="bf864-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf864-110">HRESULT</span></span>|<span data-ttu-id="bf864-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf864-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf864-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf864-112">S_OK</span></span>|`Alloc` <span data-ttu-id="bf864-113">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bf864-113">returned successfully.</span></span>|  
|<span data-ttu-id="bf864-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bf864-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf864-115">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bf864-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bf864-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf864-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf864-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bf864-117">The call timed out.</span></span>|  
|<span data-ttu-id="bf864-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf864-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf864-119">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bf864-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf864-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf864-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf864-121">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="bf864-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf864-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf864-122">E_FAIL</span></span>|<span data-ttu-id="bf864-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bf864-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf864-124">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bf864-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf864-125">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bf864-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bf864-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bf864-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bf864-127">Não havia memória suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="bf864-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf864-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf864-128">Remarks</span></span>  
 <span data-ttu-id="bf864-129">O CLR obtém um ponteiro de interface para um `IHostMalloc` instância chamando o [ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bf864-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf864-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf864-130">Requirements</span></span>  
 <span data-ttu-id="bf864-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf864-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf864-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf864-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf864-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bf864-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="bf864-134">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bf864-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bf864-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf864-135">See also</span></span>

- [<span data-ttu-id="bf864-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="bf864-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="bf864-137">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="bf864-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
