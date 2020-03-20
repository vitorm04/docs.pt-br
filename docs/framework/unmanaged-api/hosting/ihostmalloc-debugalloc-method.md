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
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178033"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="420af-102">Método IHostMAlloc::DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="420af-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="420af-103">Solicita que o host aloque a quantidade especificada de memória do heap e, adicionalmente, rastreie onde a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="420af-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="420af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="420af-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="420af-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="420af-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="420af-106">[em] O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="420af-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="420af-107">[em] Um dos valores [eMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) indicando o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="420af-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="420af-108">[em] O arquivo de código do executável sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="420af-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="420af-109">[em] O número `pszFileName` da linha em que a alocação foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="420af-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="420af-110">[fora] Um ponteiro para a memória alocada ou nulo se a solicitação não puder ser concluída.</span><span class="sxs-lookup"><span data-stu-id="420af-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="420af-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="420af-111">Return Value</span></span>  
  
|<span data-ttu-id="420af-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="420af-112">HRESULT</span></span>|<span data-ttu-id="420af-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="420af-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="420af-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="420af-114">S_OK</span></span>|<span data-ttu-id="420af-115">`DebugAlloc`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="420af-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="420af-116">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="420af-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="420af-117">A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="420af-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="420af-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="420af-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="420af-119">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="420af-119">The call timed out.</span></span>|  
|<span data-ttu-id="420af-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="420af-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="420af-121">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="420af-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="420af-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="420af-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="420af-123">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="420af-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="420af-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="420af-124">E_FAIL</span></span>|<span data-ttu-id="420af-125">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="420af-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="420af-126">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="420af-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="420af-127">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="420af-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="420af-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="420af-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="420af-129">Não havia memória suficiente para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="420af-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="420af-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="420af-130">Remarks</span></span>  
 <span data-ttu-id="420af-131">O CLR obtém um ponteiro de interface para uma instância [iHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) chamando o método [IHostMemoryManager::CreateMalloc.](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)</span><span class="sxs-lookup"><span data-stu-id="420af-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="420af-132">`DebugAlloc`permite que o tempo de execução obtenha informações de arquivo de código para uso durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="420af-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="420af-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="420af-133">Requirements</span></span>  
 <span data-ttu-id="420af-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="420af-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="420af-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="420af-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="420af-136">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="420af-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="420af-137">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="420af-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420af-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="420af-138">See also</span></span>

- [<span data-ttu-id="420af-139">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="420af-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="420af-140">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="420af-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
