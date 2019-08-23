---
title: Interface IMethodMalloc
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c67ce15175f8667139f99cec1ed17531eab473e1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935654"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="ce9e6-102">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="ce9e6-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="ce9e6-103">Fornece um método para alocar memória para um novo corpo de função da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="ce9e6-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce9e6-104">A `IMethodMalloc` interface é um alocador de memória simples.</span><span class="sxs-lookup"><span data-stu-id="ce9e6-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="ce9e6-105">Ele permite que você aloque memória, mas não a libere.</span><span class="sxs-lookup"><span data-stu-id="ce9e6-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce9e6-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="ce9e6-106">Methods</span></span>  
  
|<span data-ttu-id="ce9e6-107">Método</span><span class="sxs-lookup"><span data-stu-id="ce9e6-107">Method</span></span>|<span data-ttu-id="ce9e6-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce9e6-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce9e6-109">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="ce9e6-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="ce9e6-110">Tenta alocar uma quantidade especificada de memória para um novo corpo de função MSIL.</span><span class="sxs-lookup"><span data-stu-id="ce9e6-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce9e6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce9e6-111">Remarks</span></span>  
 <span data-ttu-id="ce9e6-112">Cada alocador é específico do módulo e garante que o corpo da função estará em um deslocamento positivo da base do módulo.</span><span class="sxs-lookup"><span data-stu-id="ce9e6-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="ce9e6-113">A memória acima da base de um módulo pode ser preciosa, portanto, o alocador deve ser usado para alocar memória apenas para um corpo de função.</span><span class="sxs-lookup"><span data-stu-id="ce9e6-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9e6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce9e6-114">Requirements</span></span>  
 <span data-ttu-id="ce9e6-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce9e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9e6-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce9e6-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce9e6-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce9e6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce9e6-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9e6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9e6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce9e6-119">See also</span></span>

- [<span data-ttu-id="ce9e6-120">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="ce9e6-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
