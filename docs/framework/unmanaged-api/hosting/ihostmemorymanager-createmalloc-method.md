---
title: Método IHostMemoryManager::CreateMAlloc
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
ms.openlocfilehash: 8bcb01f4a19e6043bd59fe6f1565cdf35ed1f77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136721"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="329ef-102">Método IHostMemoryManager::CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="329ef-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="329ef-103">Obtém um ponteiro de interface para uma instância de [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) que é usada para fazer solicitações de alocação de um heap criado pelo host.</span><span class="sxs-lookup"><span data-stu-id="329ef-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329ef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="329ef-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="329ef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="329ef-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="329ef-106">no Uma combinação de sinalizadores [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) que especifica as características da memória que está sendo alocada.</span><span class="sxs-lookup"><span data-stu-id="329ef-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="329ef-107">fora Um ponteiro para o endereço de uma instância de `IHostMAlloc` fornecida pelo host.</span><span class="sxs-lookup"><span data-stu-id="329ef-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="329ef-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="329ef-108">Return Value</span></span>  
  
|<span data-ttu-id="329ef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="329ef-109">HRESULT</span></span>|<span data-ttu-id="329ef-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="329ef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="329ef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="329ef-111">S_OK</span></span>|<span data-ttu-id="329ef-112">`CreateMAlloc` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="329ef-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="329ef-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="329ef-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="329ef-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="329ef-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="329ef-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="329ef-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="329ef-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="329ef-116">The call timed out.</span></span>|  
|<span data-ttu-id="329ef-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="329ef-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="329ef-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="329ef-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="329ef-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="329ef-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="329ef-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="329ef-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="329ef-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="329ef-121">E_FAIL</span></span>|<span data-ttu-id="329ef-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="329ef-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="329ef-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="329ef-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="329ef-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="329ef-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="329ef-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="329ef-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="329ef-126">Não há memória física suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="329ef-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="329ef-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="329ef-127">Remarks</span></span>  
 <span data-ttu-id="329ef-128">`CreateMAlloc` retorna um objeto que permite que o CLR faça solicitações de alocação por meio do host em vez de usar as funções padrão do Win32.</span><span class="sxs-lookup"><span data-stu-id="329ef-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="329ef-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="329ef-129">Requirements</span></span>  
 <span data-ttu-id="329ef-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="329ef-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="329ef-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="329ef-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="329ef-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="329ef-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="329ef-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="329ef-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329ef-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="329ef-134">See also</span></span>

- [<span data-ttu-id="329ef-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="329ef-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="329ef-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="329ef-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
