---
title: Método IHostMAlloc::Free
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6de6d12322e29ddcc854f6b9aed0a4790af089e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780718"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="b1732-102">Método IHostMAlloc::Free</span><span class="sxs-lookup"><span data-stu-id="b1732-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="b1732-103">Libera a memória que foi alocada usando o [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) função.</span><span class="sxs-lookup"><span data-stu-id="b1732-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1732-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1732-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1732-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1732-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="b1732-106">[in] Um ponteiro para a memória a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="b1732-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1732-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b1732-107">Return Value</span></span>  
  
|<span data-ttu-id="b1732-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1732-108">HRESULT</span></span>|<span data-ttu-id="b1732-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1732-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1732-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1732-110">S_OK</span></span>|<span data-ttu-id="b1732-111">`Free` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b1732-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="b1732-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1732-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1732-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b1732-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1732-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1732-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1732-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b1732-115">The call timed out.</span></span>|  
|<span data-ttu-id="b1732-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1732-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1732-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b1732-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1732-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1732-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1732-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="b1732-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1732-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1732-120">E_FAIL</span></span>|<span data-ttu-id="b1732-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b1732-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1732-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b1732-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1732-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b1732-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1732-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b1732-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b1732-125">Foi feita uma tentativa para liberar a memória que não foi alocada por meio do host.</span><span class="sxs-lookup"><span data-stu-id="b1732-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1732-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1732-126">Remarks</span></span>  
 <span data-ttu-id="b1732-127">Se o `pMem` parâmetro refere-se para uma região de memória que não foi alocada usando uma chamada para `Alloc`, o host deve retornar HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="b1732-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1732-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1732-128">Requirements</span></span>  
 <span data-ttu-id="b1732-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1732-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1732-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1732-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1732-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b1732-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1732-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1732-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1732-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1732-133">See also</span></span>

- [<span data-ttu-id="b1732-134">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="b1732-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="b1732-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="b1732-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
