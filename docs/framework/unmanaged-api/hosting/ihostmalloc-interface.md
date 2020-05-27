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
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804611"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="3a2bc-102">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="3a2bc-102">IHostMalloc Interface</span></span>
<span data-ttu-id="3a2bc-103">Fornece métodos que permitem que o Common Language Runtime (CLR) solicite alocações refinadas do heap por meio do host.</span><span class="sxs-lookup"><span data-stu-id="3a2bc-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a2bc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a2bc-104">Methods</span></span>  
  
|<span data-ttu-id="3a2bc-105">Método</span><span class="sxs-lookup"><span data-stu-id="3a2bc-105">Method</span></span>|<span data-ttu-id="3a2bc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a2bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a2bc-107">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="3a2bc-107">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="3a2bc-108">Solicita que o host aloque a quantidade solicitada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="3a2bc-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="3a2bc-109">Método DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="3a2bc-109">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="3a2bc-110">Solicita que o host aloque a quantidade solicitada de memória do heap e rastreie também onde a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="3a2bc-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="3a2bc-111">Método Free</span><span class="sxs-lookup"><span data-stu-id="3a2bc-111">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="3a2bc-112">Libera a memória que foi alocada usando o `Alloc` método.</span><span class="sxs-lookup"><span data-stu-id="3a2bc-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a2bc-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a2bc-113">Remarks</span></span>  
 <span data-ttu-id="3a2bc-114">O CLR Obtém um ponteiro de interface para uma `IHostMalloc` instância chamando o método [IHostMemoryManager:: CreateMAlloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3a2bc-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a2bc-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a2bc-115">Requirements</span></span>  
 <span data-ttu-id="3a2bc-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a2bc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a2bc-117">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3a2bc-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a2bc-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3a2bc-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a2bc-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a2bc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a2bc-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a2bc-120">See also</span></span>

- [<span data-ttu-id="3a2bc-121">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="3a2bc-121">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="3a2bc-122">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="3a2bc-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
