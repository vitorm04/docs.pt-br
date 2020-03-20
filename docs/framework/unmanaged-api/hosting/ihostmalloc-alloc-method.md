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
ms.openlocfilehash: dded37fdef02963f60883b289462aa6a96693b3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176299"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="91027-102">Método IHostMAlloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="91027-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="91027-103">Solicita que o host aloque a quantidade especificada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="91027-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91027-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91027-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91027-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="91027-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="91027-106">[em] O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="91027-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="91027-107">[em] Um dos valores [eMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) indicando o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="91027-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="91027-108">[fora] Um ponteiro para a memória alocada ou nulo se a solicitação não puder ser concluída.</span><span class="sxs-lookup"><span data-stu-id="91027-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91027-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="91027-109">Return Value</span></span>  
  
|<span data-ttu-id="91027-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91027-110">HRESULT</span></span>|<span data-ttu-id="91027-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="91027-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91027-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="91027-112">S_OK</span></span>|<span data-ttu-id="91027-113">`Alloc`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="91027-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="91027-114">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="91027-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91027-115">O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="91027-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91027-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91027-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91027-117">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="91027-117">The call timed out.</span></span>|  
|<span data-ttu-id="91027-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91027-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91027-119">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="91027-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91027-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91027-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91027-121">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="91027-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91027-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91027-122">E_FAIL</span></span>|<span data-ttu-id="91027-123">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="91027-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91027-124">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="91027-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91027-125">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="91027-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="91027-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="91027-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="91027-127">Não havia memória suficiente para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="91027-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91027-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="91027-128">Remarks</span></span>  
 <span data-ttu-id="91027-129">O CLR obtém um `IHostMalloc` ponteiro de interface em uma instância chamando o [método IHostMemoryManager::CreateMalloc.](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)</span><span class="sxs-lookup"><span data-stu-id="91027-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91027-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91027-130">Requirements</span></span>  
 <span data-ttu-id="91027-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91027-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91027-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="91027-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91027-133">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91027-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91027-134">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91027-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91027-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="91027-135">See also</span></span>

- [<span data-ttu-id="91027-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="91027-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="91027-137">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="91027-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
