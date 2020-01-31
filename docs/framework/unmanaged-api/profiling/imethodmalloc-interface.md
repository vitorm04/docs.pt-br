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
ms.openlocfilehash: e9cbf4551c2f8b183e9e6c37a74b13aff3a19ec1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860950"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="24922-102">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="24922-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="24922-103">Fornece um método para alocar memória para um novo corpo de função da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="24922-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24922-104">A interface `IMethodMalloc` é um alocador de memória simples.</span><span class="sxs-lookup"><span data-stu-id="24922-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="24922-105">Ele permite que você aloque memória, mas não a libere.</span><span class="sxs-lookup"><span data-stu-id="24922-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24922-106">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="24922-106">Methods</span></span>  
  
|<span data-ttu-id="24922-107">Método</span><span class="sxs-lookup"><span data-stu-id="24922-107">Method</span></span>|<span data-ttu-id="24922-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="24922-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24922-109">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="24922-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="24922-110">Tenta alocar uma quantidade especificada de memória para um novo corpo de função MSIL.</span><span class="sxs-lookup"><span data-stu-id="24922-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24922-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="24922-111">Remarks</span></span>  
 <span data-ttu-id="24922-112">Cada alocador é específico do módulo e garante que o corpo da função estará em um deslocamento positivo da base do módulo.</span><span class="sxs-lookup"><span data-stu-id="24922-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="24922-113">A memória acima da base de um módulo pode ser preciosa, portanto, o alocador deve ser usado para alocar memória apenas para um corpo de função.</span><span class="sxs-lookup"><span data-stu-id="24922-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24922-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="24922-114">Requirements</span></span>  
 <span data-ttu-id="24922-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24922-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24922-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="24922-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24922-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24922-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24922-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24922-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24922-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="24922-119">See also</span></span>

- [<span data-ttu-id="24922-120">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="24922-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
