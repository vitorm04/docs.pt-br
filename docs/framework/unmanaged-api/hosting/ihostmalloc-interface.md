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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2a7a29ef1dc85c2ad554995286e5137fcb104be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757632"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="ccbfa-102">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="ccbfa-102">IHostMalloc Interface</span></span>
<span data-ttu-id="ccbfa-103">Fornece métodos que permitem que o common language runtime (CLR) para solicitar refinadas alocações do heap por meio do host.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccbfa-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ccbfa-104">Methods</span></span>  
  
|<span data-ttu-id="ccbfa-105">Método</span><span class="sxs-lookup"><span data-stu-id="ccbfa-105">Method</span></span>|<span data-ttu-id="ccbfa-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccbfa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccbfa-107">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="ccbfa-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="ccbfa-108">Solicita que o host alocar a quantidade solicitada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="ccbfa-109">Método DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="ccbfa-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="ccbfa-110">Solicita que o host alocar a quantidade solicitada de memória do heap e, além disso, controlar em que a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="ccbfa-111">Método Free</span><span class="sxs-lookup"><span data-stu-id="ccbfa-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="ccbfa-112">Libera a memória que foi alocada usando o `Alloc` método.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccbfa-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="ccbfa-113">Remarks</span></span>  
 <span data-ttu-id="ccbfa-114">O CLR obtém um ponteiro de interface para um `IHostMalloc` instância chamando o [ihostmemorymanager:: Createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccbfa-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ccbfa-115">Requirements</span></span>  
 <span data-ttu-id="ccbfa-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccbfa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccbfa-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ccbfa-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ccbfa-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ccbfa-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccbfa-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccbfa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbfa-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccbfa-120">See also</span></span>

- [<span data-ttu-id="ccbfa-121">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="ccbfa-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="ccbfa-122">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ccbfa-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
