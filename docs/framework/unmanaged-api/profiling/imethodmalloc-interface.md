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
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077756"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="ec329-102">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="ec329-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="ec329-103">Fornece um método para alocar memória para um novo corpo de função do Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="ec329-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec329-104">O `IMethodMalloc` interface é um alocador de memória simples.</span><span class="sxs-lookup"><span data-stu-id="ec329-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="ec329-105">Ele permite que você alocar memória, mas não para liberá-la.</span><span class="sxs-lookup"><span data-stu-id="ec329-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec329-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="ec329-106">Methods</span></span>  
  
|<span data-ttu-id="ec329-107">Método</span><span class="sxs-lookup"><span data-stu-id="ec329-107">Method</span></span>|<span data-ttu-id="ec329-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec329-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec329-109">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="ec329-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="ec329-110">Tenta alocar uma quantidade especificada de memória para um novo corpo de função MSIL.</span><span class="sxs-lookup"><span data-stu-id="ec329-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec329-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec329-111">Remarks</span></span>  
 <span data-ttu-id="ec329-112">Cada alocador é específica do módulo e garante que o corpo da função esteja em um deslocamento positivo da base do módulo.</span><span class="sxs-lookup"><span data-stu-id="ec329-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="ec329-113">Memória acima a base de um módulo pode ser preciosa, portanto, o alocador deve ser usado para alocar memória para o corpo da função.</span><span class="sxs-lookup"><span data-stu-id="ec329-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec329-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec329-114">Requirements</span></span>  
 <span data-ttu-id="ec329-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec329-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec329-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec329-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec329-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec329-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ec329-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ec329-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ec329-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec329-119">See also</span></span>

- [<span data-ttu-id="ec329-120">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="ec329-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
