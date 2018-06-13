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
ms.openlocfilehash: bbf889aaa6a78e67d0f08758adc0bf31cd932e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441342"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="5744f-102">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="5744f-102">IHostMalloc Interface</span></span>
<span data-ttu-id="5744f-103">Fornece métodos que permitem que o common language runtime (CLR) para solicitar refinadas alocações de heap por meio do host.</span><span class="sxs-lookup"><span data-stu-id="5744f-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5744f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5744f-104">Methods</span></span>  
  
|<span data-ttu-id="5744f-105">Método</span><span class="sxs-lookup"><span data-stu-id="5744f-105">Method</span></span>|<span data-ttu-id="5744f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5744f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5744f-107">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="5744f-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="5744f-108">Solicita que o host aloque a quantidade solicitada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="5744f-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="5744f-109">Método DebugAlloc</span><span class="sxs-lookup"><span data-stu-id="5744f-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="5744f-110">Solicita que o host aloque a quantidade solicitada de memória de heap e Além disso, controlar em que a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="5744f-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="5744f-111">Método Free</span><span class="sxs-lookup"><span data-stu-id="5744f-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="5744f-112">Libera a memória foi alocada usando o `Alloc` método.</span><span class="sxs-lookup"><span data-stu-id="5744f-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5744f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="5744f-113">Remarks</span></span>  
 <span data-ttu-id="5744f-114">O CLR obtém um ponteiro de interface para um `IHostMalloc` instância chamando o [Ihostmemorymanager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5744f-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5744f-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5744f-115">Requirements</span></span>  
 <span data-ttu-id="5744f-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5744f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5744f-117">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5744f-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5744f-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5744f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5744f-119">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5744f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5744f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5744f-120">See Also</span></span>  
 [<span data-ttu-id="5744f-121">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="5744f-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="5744f-122">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="5744f-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
