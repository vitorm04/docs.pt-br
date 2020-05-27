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
ms.openlocfilehash: 89c1d7b043d4369bf16a851924711c3c9d75791e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804526"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="d373c-102">Método IHostMemoryManager::CreateMAlloc</span><span class="sxs-lookup"><span data-stu-id="d373c-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="d373c-103">Obtém um ponteiro de interface para uma instância de [IHostMAlloc](ihostmalloc-interface.md) que é usada para fazer solicitações de alocação de um heap criado pelo host.</span><span class="sxs-lookup"><span data-stu-id="d373c-103">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d373c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d373c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d373c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d373c-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="d373c-106">no Uma combinação de sinalizadores de [MALLOC_TYPE](malloc-type-enumeration.md) que especifica as características da memória que está sendo alocada.</span><span class="sxs-lookup"><span data-stu-id="d373c-106">[in] A combination of [MALLOC_TYPE](malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="d373c-107">fora Um ponteiro para o endereço de uma `IHostMAlloc` instância fornecida pelo host.</span><span class="sxs-lookup"><span data-stu-id="d373c-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d373c-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="d373c-108">Return Value</span></span>  
  
|<span data-ttu-id="d373c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d373c-109">HRESULT</span></span>|<span data-ttu-id="d373c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d373c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d373c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d373c-111">S_OK</span></span>|<span data-ttu-id="d373c-112">`CreateMAlloc`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d373c-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="d373c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d373c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d373c-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d373c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d373c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d373c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d373c-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d373c-116">The call timed out.</span></span>|  
|<span data-ttu-id="d373c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d373c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d373c-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d373c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d373c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d373c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d373c-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="d373c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d373c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d373c-121">E_FAIL</span></span>|<span data-ttu-id="d373c-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d373c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d373c-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="d373c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d373c-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d373c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d373c-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d373c-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d373c-126">Não há memória física suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="d373c-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d373c-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="d373c-127">Remarks</span></span>  
 <span data-ttu-id="d373c-128">`CreateMAlloc`Retorna um objeto que permite que o CLR faça solicitações de alocação por meio do host em vez de usar as funções padrão do Win32.</span><span class="sxs-lookup"><span data-stu-id="d373c-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d373c-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d373c-129">Requirements</span></span>  
 <span data-ttu-id="d373c-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d373c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d373c-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d373c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d373c-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d373c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d373c-133">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d373c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d373c-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="d373c-134">See also</span></span>

- [<span data-ttu-id="d373c-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="d373c-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="d373c-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="d373c-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
