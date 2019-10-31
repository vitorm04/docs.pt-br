---
title: Interface IHostMalloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: abc6cca185b318be016f92ac8c97d21f7af5940a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136772"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="b6aaf-102">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="b6aaf-102">IHostMalloc Interface</span></span>
<span data-ttu-id="b6aaf-103">Fornece métodos que permitem que o Common Language Runtime (CLR) solicite alocações refinadas do heap por meio do host.</span><span class="sxs-lookup"><span data-stu-id="b6aaf-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6aaf-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b6aaf-104">Methods</span></span>  
  
|<span data-ttu-id="b6aaf-105">Método</span><span class="sxs-lookup"><span data-stu-id="b6aaf-105">Method</span></span>|<span data-ttu-id="b6aaf-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6aaf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6aaf-107">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="b6aaf-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="b6aaf-108">Solicita que o host aloque a quantidade solicitada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="b6aaf-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="b6aaf-109">Método DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="b6aaf-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="b6aaf-110">Solicita que o host aloque a quantidade solicitada de memória do heap e rastreie também onde a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="b6aaf-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="b6aaf-111">Método Free</span><span class="sxs-lookup"><span data-stu-id="b6aaf-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="b6aaf-112">Libera a memória que foi alocada usando o método `Alloc`.</span><span class="sxs-lookup"><span data-stu-id="b6aaf-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6aaf-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6aaf-113">Remarks</span></span>  
 <span data-ttu-id="b6aaf-114">O CLR Obtém um ponteiro de interface para uma instância de `IHostMalloc` chamando o método [IHostMemoryManager:: CreateMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6aaf-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6aaf-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6aaf-115">Requirements</span></span>  
 <span data-ttu-id="b6aaf-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6aaf-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6aaf-117">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6aaf-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6aaf-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6aaf-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6aaf-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6aaf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6aaf-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6aaf-120">See also</span></span>

- [<span data-ttu-id="b6aaf-121">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="b6aaf-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="b6aaf-122">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b6aaf-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
