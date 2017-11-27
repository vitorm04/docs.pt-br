---
title: Interface ICorProfilerThreadEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum
helpviewer_keywords: ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2ce48c836070018059becd1ece269ce7c878c7ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="f3bc3-102">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="f3bc3-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="f3bc3-103">Fornece métodos para iterar em sequência por meio de uma coleção de segmentos no common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3bc3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f3bc3-104">Methods</span></span>  
  
|<span data-ttu-id="f3bc3-105">Método</span><span class="sxs-lookup"><span data-stu-id="f3bc3-105">Method</span></span>|<span data-ttu-id="f3bc3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3bc3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3bc3-107">Método clone</span><span class="sxs-lookup"><span data-stu-id="f3bc3-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="f3bc3-108">Obtém um ponteiro de interface para uma cópia deste `ICorProfilerThreadEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="f3bc3-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="f3bc3-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="f3bc3-110">Obtém o número de threads que são usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="f3bc3-111">Próximo método</span><span class="sxs-lookup"><span data-stu-id="f3bc3-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="f3bc3-112">Obtém o número especificado de threads de contíguas de uma coleção sequencial de threads, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="f3bc3-113">Método Reset</span><span class="sxs-lookup"><span data-stu-id="f3bc3-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="f3bc3-114">Move o cursor do enumerador para a posição inicial da sequência de.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="f3bc3-115">Método Skip</span><span class="sxs-lookup"><span data-stu-id="f3bc3-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="f3bc3-116">Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3bc3-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3bc3-117">Remarks</span></span>  
 <span data-ttu-id="f3bc3-118">O `ICorProfilerThreadEnum` interface é um enumerador.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="f3bc3-119">Ele permite que o destinatário de uma matriz para elementos de pull do remetente a uma taxa que é apropriado para o receptor.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="f3bc3-120">Em outras palavras, o destinatário é capaz de controlar explicitamente o fluxo de elementos da matriz, evitando, assim, os problemas associados à transmitindo matrizes grandes como parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3bc3-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3bc3-121">Requirements</span></span>  
 <span data-ttu-id="f3bc3-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3bc3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3bc3-123">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3bc3-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3bc3-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3bc3-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3bc3-125">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3bc3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bc3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3bc3-126">See Also</span></span>  
 [<span data-ttu-id="f3bc3-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f3bc3-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="f3bc3-128">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f3bc3-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
