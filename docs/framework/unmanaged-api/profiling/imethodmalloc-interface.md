---
title: Interface IMethodMalloc
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1941a46a60219d9dd56d162f89baf268f220c102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="e6969-102">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="e6969-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="e6969-103">Fornece um método para alocar memória para um novo corpo de função do Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="e6969-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6969-104">O `IMethodMalloc` interface é um alocador de memória simples.</span><span class="sxs-lookup"><span data-stu-id="e6969-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="e6969-105">Ele permite que você alocar memória, mas não para liberá-la.</span><span class="sxs-lookup"><span data-stu-id="e6969-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6969-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="e6969-106">Methods</span></span>  
  
|<span data-ttu-id="e6969-107">Método</span><span class="sxs-lookup"><span data-stu-id="e6969-107">Method</span></span>|<span data-ttu-id="e6969-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6969-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6969-109">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="e6969-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="e6969-110">Tenta alocar uma quantidade especificada de memória para um novo corpo de função MSIL.</span><span class="sxs-lookup"><span data-stu-id="e6969-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6969-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6969-111">Remarks</span></span>  
 <span data-ttu-id="e6969-112">Cada alocador é específico do módulo e garante que o corpo da função estará em um deslocamento positivo de base do módulo.</span><span class="sxs-lookup"><span data-stu-id="e6969-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="e6969-113">Memória acima de base de um módulo pode ser preciosa, portanto, o alocador de deve ser usado para alocar memória para o corpo da função.</span><span class="sxs-lookup"><span data-stu-id="e6969-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6969-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6969-114">Requirements</span></span>  
 <span data-ttu-id="e6969-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6969-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6969-116">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e6969-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6969-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6969-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6969-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6969-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6969-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6969-119">See Also</span></span>  
 [<span data-ttu-id="e6969-120">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e6969-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
