---
title: "Método IHostMAlloc::Free"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Free
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ac361f939a134aa6d2bc8b215c5d447b352466e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="53b76-102">Método IHostMAlloc::Free</span><span class="sxs-lookup"><span data-stu-id="53b76-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="53b76-103">Libera a memória foi alocada usando o [alocação](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) função.</span><span class="sxs-lookup"><span data-stu-id="53b76-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b76-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53b76-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53b76-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53b76-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="53b76-106">[in] Um ponteiro para a memória a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="53b76-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53b76-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="53b76-107">Return Value</span></span>  
  
|<span data-ttu-id="53b76-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53b76-108">HRESULT</span></span>|<span data-ttu-id="53b76-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="53b76-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53b76-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="53b76-110">S_OK</span></span>|<span data-ttu-id="53b76-111">`Free`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="53b76-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="53b76-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53b76-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53b76-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="53b76-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53b76-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53b76-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53b76-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="53b76-115">The call timed out.</span></span>|  
|<span data-ttu-id="53b76-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53b76-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53b76-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="53b76-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53b76-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53b76-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53b76-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="53b76-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53b76-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53b76-120">E_FAIL</span></span>|<span data-ttu-id="53b76-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="53b76-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53b76-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="53b76-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53b76-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53b76-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="53b76-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="53b76-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="53b76-125">Foi feita uma tentativa para liberar a memória que não foi alocada por meio do host.</span><span class="sxs-lookup"><span data-stu-id="53b76-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53b76-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="53b76-126">Remarks</span></span>  
 <span data-ttu-id="53b76-127">Se o `pMem` parâmetro faz referência a uma região de memória que não foi alocada por meio de uma chamada para `Alloc`, o host deve retornar HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="53b76-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53b76-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53b76-128">Requirements</span></span>  
 <span data-ttu-id="53b76-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53b76-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53b76-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53b76-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53b76-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="53b76-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53b76-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53b76-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b76-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53b76-133">See Also</span></span>  
 [<span data-ttu-id="53b76-134">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="53b76-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="53b76-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="53b76-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
