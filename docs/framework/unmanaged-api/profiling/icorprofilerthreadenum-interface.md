---
title: Interface ICorProfilerThreadEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47359cd71460732100364f07e0dc5efacc44c760
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092039"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="31179-102">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="31179-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="31179-103">Fornece métodos para iterar de forma sequencial por meio de uma coleção de segmentos no common language runtime.</span><span class="sxs-lookup"><span data-stu-id="31179-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31179-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="31179-104">Methods</span></span>  
  
|<span data-ttu-id="31179-105">Método</span><span class="sxs-lookup"><span data-stu-id="31179-105">Method</span></span>|<span data-ttu-id="31179-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="31179-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31179-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="31179-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="31179-108">Obtém um ponteiro de interface para uma cópia deste `ICorProfilerThreadEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="31179-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="31179-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="31179-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="31179-110">Obtém o número de threads que são usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31179-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="31179-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="31179-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="31179-112">Obtém o número especificado de threads contíguos de uma coleção sequencial de threads, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="31179-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="31179-113">Método Reset</span><span class="sxs-lookup"><span data-stu-id="31179-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="31179-114">Move o cursor do enumerador para a posição inicial da sequência.</span><span class="sxs-lookup"><span data-stu-id="31179-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="31179-115">Método Skip</span><span class="sxs-lookup"><span data-stu-id="31179-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="31179-116">Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.</span><span class="sxs-lookup"><span data-stu-id="31179-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31179-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="31179-117">Remarks</span></span>  
 <span data-ttu-id="31179-118">O `ICorProfilerThreadEnum` interface é um enumerador.</span><span class="sxs-lookup"><span data-stu-id="31179-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="31179-119">Ele permite que o destinatário de uma matriz a elementos de pull do remetente de uma taxa que é apropriado para o receptor.</span><span class="sxs-lookup"><span data-stu-id="31179-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="31179-120">Em outras palavras, o destinatário é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando assim os problemas associados com a passagem de matrizes grandes como parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="31179-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31179-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31179-121">Requirements</span></span>  
 <span data-ttu-id="31179-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31179-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31179-123">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31179-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31179-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31179-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="31179-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="31179-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="31179-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31179-126">See also</span></span>

- [<span data-ttu-id="31179-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="31179-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="31179-128">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="31179-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
