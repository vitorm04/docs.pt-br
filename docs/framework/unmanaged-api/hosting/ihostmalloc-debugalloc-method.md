---
title: Método IHostMAlloc::DebugAlloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: a2a752f23ed64795f9208b9101c21bc585d5f431
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136811"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="6c008-102">Método IHostMAlloc::DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="6c008-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="6c008-103">Solicita que o host aloque a quantidade especificada de memória do heap, além de controlar onde a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="6c008-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c008-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c008-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c008-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c008-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="6c008-106">no O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="6c008-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="6c008-107">no Um dos valores de [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) , indicando o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="6c008-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="6c008-108">no O arquivo de código do executável que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="6c008-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="6c008-109">no O número de linha em `pszFileName` em que a alocação foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="6c008-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="6c008-110">fora Um ponteiro para a memória alocada ou NULL se a solicitação não puder ser concluída.</span><span class="sxs-lookup"><span data-stu-id="6c008-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c008-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6c008-111">Return Value</span></span>  
  
|<span data-ttu-id="6c008-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c008-112">HRESULT</span></span>|<span data-ttu-id="6c008-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c008-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c008-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c008-114">S_OK</span></span>|<span data-ttu-id="6c008-115">`DebugAlloc` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6c008-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="6c008-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c008-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c008-117">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6c008-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c008-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c008-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c008-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6c008-119">The call timed out.</span></span>|  
|<span data-ttu-id="6c008-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c008-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c008-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6c008-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c008-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c008-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c008-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="6c008-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c008-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c008-124">E_FAIL</span></span>|<span data-ttu-id="6c008-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6c008-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c008-126">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="6c008-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c008-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6c008-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6c008-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6c008-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6c008-129">Não havia memória suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="6c008-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c008-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c008-130">Remarks</span></span>  
 <span data-ttu-id="6c008-131">O CLR Obtém um ponteiro de interface para uma instância [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) chamando o método [IHostMemoryManager:: CreateMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6c008-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="6c008-132">`DebugAlloc` permite que o tempo de execução Obtenha informações de arquivo de código para uso durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="6c008-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c008-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c008-133">Requirements</span></span>  
 <span data-ttu-id="6c008-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c008-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c008-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c008-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c008-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c008-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c008-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c008-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c008-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c008-138">See also</span></span>

- [<span data-ttu-id="6c008-139">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="6c008-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="6c008-140">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="6c008-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
