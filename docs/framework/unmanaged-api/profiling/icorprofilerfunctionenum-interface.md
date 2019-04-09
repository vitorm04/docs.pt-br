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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e77ec9de198b673bb3b5fc4dad3cd1b0316f07c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092065"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="04cfa-102">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="04cfa-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="04cfa-103">Fornece métodos para iterar de forma sequencial por meio de uma coleção de funções no common language runtime.</span><span class="sxs-lookup"><span data-stu-id="04cfa-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04cfa-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="04cfa-104">Methods</span></span>  
  
|<span data-ttu-id="04cfa-105">Método</span><span class="sxs-lookup"><span data-stu-id="04cfa-105">Method</span></span>|<span data-ttu-id="04cfa-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="04cfa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04cfa-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="04cfa-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="04cfa-108">Obtém um ponteiro de interface para uma cópia deste `ICorProfilerFunctionEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="04cfa-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="04cfa-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="04cfa-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="04cfa-110">Obtém o número de funções que foram carregados pelo aplicativo ou à força pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="04cfa-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="04cfa-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="04cfa-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="04cfa-112">Obtém o número especificado de funções contíguos de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="04cfa-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="04cfa-113">Método Reset</span><span class="sxs-lookup"><span data-stu-id="04cfa-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="04cfa-114">Move o cursor do enumerador para a posição inicial da sequência.</span><span class="sxs-lookup"><span data-stu-id="04cfa-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="04cfa-115">Método Skip</span><span class="sxs-lookup"><span data-stu-id="04cfa-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="04cfa-116">Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos é ignorado.</span><span class="sxs-lookup"><span data-stu-id="04cfa-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04cfa-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="04cfa-117">Remarks</span></span>  
 <span data-ttu-id="04cfa-118">O `ICorProfilerFunctionEnum` interface é um enumerador.</span><span class="sxs-lookup"><span data-stu-id="04cfa-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="04cfa-119">Ele permite que o destinatário de uma matriz a elementos de pull do remetente de uma taxa que é apropriado para o receptor.</span><span class="sxs-lookup"><span data-stu-id="04cfa-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="04cfa-120">Em outras palavras, o destinatário é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando assim os problemas associados com a passagem de matrizes grandes como parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="04cfa-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 `ICorProfilerFunctionEnum` <span data-ttu-id="04cfa-121">Enumera em funções que já foram compilados pelo JIT, mas não incluem funções que são carregadas de imagens nativas geradas com Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="04cfa-121">enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04cfa-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04cfa-122">Requirements</span></span>  
 <span data-ttu-id="04cfa-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04cfa-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04cfa-124">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04cfa-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04cfa-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04cfa-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="04cfa-126">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="04cfa-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="04cfa-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04cfa-127">See also</span></span>

- [<span data-ttu-id="04cfa-128">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="04cfa-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="04cfa-129">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="04cfa-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="04cfa-130">Método EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="04cfa-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
