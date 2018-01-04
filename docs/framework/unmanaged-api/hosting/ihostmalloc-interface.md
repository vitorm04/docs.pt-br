---
title: Interface IHostMalloc
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1690f5fe8f1417e6547ed94db8c71f079ebf5e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="ac42c-102">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="ac42c-102">IHostMalloc Interface</span></span>
<span data-ttu-id="ac42c-103">Fornece métodos que permitem que o common language runtime (CLR) para solicitar refinadas alocações de heap por meio do host.</span><span class="sxs-lookup"><span data-stu-id="ac42c-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac42c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ac42c-104">Methods</span></span>  
  
|<span data-ttu-id="ac42c-105">Método</span><span class="sxs-lookup"><span data-stu-id="ac42c-105">Method</span></span>|<span data-ttu-id="ac42c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac42c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac42c-107">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="ac42c-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="ac42c-108">Solicita que o host aloque a quantidade solicitada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="ac42c-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="ac42c-109">Método DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="ac42c-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="ac42c-110">Solicita que o host aloque a quantidade solicitada de memória de heap e Além disso, controlar em que a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="ac42c-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="ac42c-111">Método Free</span><span class="sxs-lookup"><span data-stu-id="ac42c-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="ac42c-112">Libera a memória foi alocada usando o `Alloc` método.</span><span class="sxs-lookup"><span data-stu-id="ac42c-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac42c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac42c-113">Remarks</span></span>  
 <span data-ttu-id="ac42c-114">O CLR obtém um ponteiro de interface para um `IHostMalloc` instância chamando o [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ac42c-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac42c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac42c-115">Requirements</span></span>  
 <span data-ttu-id="ac42c-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac42c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac42c-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac42c-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac42c-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ac42c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac42c-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac42c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac42c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac42c-120">See Also</span></span>  
 [<span data-ttu-id="ac42c-121">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="ac42c-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="ac42c-122">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ac42c-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
