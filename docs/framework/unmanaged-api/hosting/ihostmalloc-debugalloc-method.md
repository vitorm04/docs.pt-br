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
ms.openlocfilehash: 8475362ede5ea28009d5abc54c286d6f2a6fed0f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804630"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="fb0f2-102">Método IHostMAlloc::DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="fb0f2-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="fb0f2-103">Solicita que o host aloque a quantidade especificada de memória do heap, além de controlar onde a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb0f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb0f2-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb0f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb0f2-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="fb0f2-106">no O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="fb0f2-107">no Um dos valores de [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) , indicando o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="fb0f2-108">no O arquivo de código do executável que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="fb0f2-109">no O número de linha em `pszFileName` que a alocação foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="fb0f2-110">fora Um ponteiro para a memória alocada ou NULL se a solicitação não puder ser concluída.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb0f2-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="fb0f2-111">Return Value</span></span>  
  
|<span data-ttu-id="fb0f2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb0f2-112">HRESULT</span></span>|<span data-ttu-id="fb0f2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb0f2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb0f2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb0f2-114">S_OK</span></span>|<span data-ttu-id="fb0f2-115">`DebugAlloc`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="fb0f2-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb0f2-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb0f2-117">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb0f2-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb0f2-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb0f2-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-119">The call timed out.</span></span>|  
|<span data-ttu-id="fb0f2-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb0f2-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb0f2-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb0f2-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb0f2-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb0f2-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb0f2-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb0f2-124">E_FAIL</span></span>|<span data-ttu-id="fb0f2-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb0f2-126">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb0f2-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fb0f2-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fb0f2-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="fb0f2-129">Não havia memória suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb0f2-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb0f2-130">Remarks</span></span>  
 <span data-ttu-id="fb0f2-131">O CLR Obtém um ponteiro de interface para uma instância [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) chamando o método [IHostMemoryManager:: CreateMAlloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fb0f2-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="fb0f2-132">`DebugAlloc`permite que o tempo de execução Obtenha informações de arquivo de código para uso durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="fb0f2-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb0f2-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb0f2-133">Requirements</span></span>  
 <span data-ttu-id="fb0f2-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb0f2-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb0f2-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb0f2-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb0f2-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fb0f2-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb0f2-137">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb0f2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb0f2-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb0f2-138">See also</span></span>

- [<span data-ttu-id="fb0f2-139">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="fb0f2-139">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="fb0f2-140">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="fb0f2-140">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
