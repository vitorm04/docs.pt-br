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
ms.openlocfilehash: 9837e4e3428a0293c8e689b3f3e081aa07f055b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192075"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="ca92c-102">Método IHostMAlloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="ca92c-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="ca92c-103">Solicita que o host aloque a quantidade especificada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="ca92c-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca92c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca92c-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca92c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca92c-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="ca92c-106">no O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="ca92c-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="ca92c-107">no Um dos valores de [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) , indicando o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="ca92c-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="ca92c-108">fora Um ponteiro para a memória alocada ou NULL se a solicitação não puder ser concluída.</span><span class="sxs-lookup"><span data-stu-id="ca92c-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca92c-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ca92c-109">Return Value</span></span>  
  
|<span data-ttu-id="ca92c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca92c-110">HRESULT</span></span>|<span data-ttu-id="ca92c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca92c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca92c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca92c-112">S_OK</span></span>|<span data-ttu-id="ca92c-113">`Alloc` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ca92c-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="ca92c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca92c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca92c-115">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ca92c-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca92c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca92c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca92c-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="ca92c-117">The call timed out.</span></span>|  
|<span data-ttu-id="ca92c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca92c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca92c-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ca92c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca92c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca92c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca92c-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="ca92c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca92c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca92c-122">E_FAIL</span></span>|<span data-ttu-id="ca92c-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ca92c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca92c-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="ca92c-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca92c-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca92c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ca92c-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ca92c-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ca92c-127">Não havia memória suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="ca92c-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca92c-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca92c-128">Remarks</span></span>  
 <span data-ttu-id="ca92c-129">O CLR Obtém um ponteiro de interface para uma instância de `IHostMalloc` chamando o método [IHostMemoryManager:: CreateMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ca92c-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca92c-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca92c-130">Requirements</span></span>  
 <span data-ttu-id="ca92c-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca92c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca92c-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca92c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca92c-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca92c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca92c-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca92c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca92c-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca92c-135">See also</span></span>

- [<span data-ttu-id="ca92c-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="ca92c-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="ca92c-137">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="ca92c-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
