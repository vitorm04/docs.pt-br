---
title: Interface ICorProfilerFunctionEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: 17f7243096b7ac18e456f8f31196055492015346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447800"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="bd08c-102">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="bd08c-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="bd08c-103">Fornece métodos para iterar em sequência por meio de uma coleção de funções no Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="bd08c-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd08c-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bd08c-104">Methods</span></span>  
  
|<span data-ttu-id="bd08c-105">Método</span><span class="sxs-lookup"><span data-stu-id="bd08c-105">Method</span></span>|<span data-ttu-id="bd08c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd08c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd08c-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="bd08c-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="bd08c-108">Obtém um ponteiro de interface para uma cópia desta `ICorProfilerFunctionEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="bd08c-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="bd08c-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="bd08c-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="bd08c-110">Obtém o número de funções que foram carregadas pelo aplicativo ou carregadas de modo forçado pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="bd08c-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="bd08c-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="bd08c-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="bd08c-112">Obtém o número especificado de funções contíguas de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="bd08c-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="bd08c-113">Método Reset</span><span class="sxs-lookup"><span data-stu-id="bd08c-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="bd08c-114">Move o cursor do enumerador para a posição inicial da sequência.</span><span class="sxs-lookup"><span data-stu-id="bd08c-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="bd08c-115">Método Skip</span><span class="sxs-lookup"><span data-stu-id="bd08c-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="bd08c-116">Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos seja ignorado.</span><span class="sxs-lookup"><span data-stu-id="bd08c-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd08c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd08c-117">Remarks</span></span>  
 <span data-ttu-id="bd08c-118">A interface `ICorProfilerFunctionEnum` é um enumerador.</span><span class="sxs-lookup"><span data-stu-id="bd08c-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="bd08c-119">Ele permite que o destinatário de uma matriz Extraia elementos do remetente a uma taxa apropriada para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="bd08c-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="bd08c-120">Em outras palavras, o receptor é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando, assim, os problemas associados à passagem de matrizes grandes como parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="bd08c-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="bd08c-121">`ICorProfilerFunctionEnum` enumera em funções que já foram compiladas por JIT, mas não inclui funções que são carregadas de imagens nativas geradas com NGen. exe.</span><span class="sxs-lookup"><span data-stu-id="bd08c-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd08c-122">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bd08c-122">Requirements</span></span>  
 <span data-ttu-id="bd08c-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd08c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd08c-124">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bd08c-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd08c-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd08c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd08c-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd08c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd08c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd08c-127">See also</span></span>

- [<span data-ttu-id="bd08c-128">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="bd08c-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="bd08c-129">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="bd08c-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="bd08c-130">Método EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="bd08c-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
