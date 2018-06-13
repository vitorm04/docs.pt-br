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
ms.openlocfilehash: a8bd7b16f06433970d1222dbeaa843e187715faa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438991"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="6e784-102">Método IHostMAlloc::Free</span><span class="sxs-lookup"><span data-stu-id="6e784-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="6e784-103">Libera a memória foi alocada usando o [alocação](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) função.</span><span class="sxs-lookup"><span data-stu-id="6e784-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e784-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e784-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e784-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e784-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="6e784-106">[in] Um ponteiro para a memória a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="6e784-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e784-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6e784-107">Return Value</span></span>  
  
|<span data-ttu-id="6e784-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e784-108">HRESULT</span></span>|<span data-ttu-id="6e784-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e784-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e784-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e784-110">S_OK</span></span>|<span data-ttu-id="6e784-111">`Free` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="6e784-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="6e784-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e784-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e784-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6e784-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6e784-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e784-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e784-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="6e784-115">The call timed out.</span></span>|  
|<span data-ttu-id="6e784-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e784-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e784-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6e784-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e784-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e784-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e784-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="6e784-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e784-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e784-120">E_FAIL</span></span>|<span data-ttu-id="6e784-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6e784-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e784-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="6e784-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e784-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6e784-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6e784-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="6e784-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="6e784-125">Foi feita uma tentativa para liberar a memória que não foi alocada por meio do host.</span><span class="sxs-lookup"><span data-stu-id="6e784-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e784-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e784-126">Remarks</span></span>  
 <span data-ttu-id="6e784-127">Se o `pMem` parâmetro faz referência a uma região de memória que não foi alocada por meio de uma chamada para `Alloc`, o host deve retornar HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="6e784-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e784-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e784-128">Requirements</span></span>  
 <span data-ttu-id="6e784-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e784-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e784-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e784-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e784-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6e784-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e784-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e784-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e784-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e784-133">See Also</span></span>  
 [<span data-ttu-id="6e784-134">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="6e784-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="6e784-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="6e784-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
