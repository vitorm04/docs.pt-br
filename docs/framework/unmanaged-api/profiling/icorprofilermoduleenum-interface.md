---
title: Interface ICorProfilerModuleEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum
api_location: mscorwks.cll
api_type: COM
f1_keywords: ICorProfilerModuleEnum
helpviewer_keywords: ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 43cc6afc42fc1a02fd7d7b3df2973cc9b3e31251
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="10dbc-102">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="10dbc-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="10dbc-103">Fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos carregados pelo aplicativo ou pelo criador de perfis.</span><span class="sxs-lookup"><span data-stu-id="10dbc-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10dbc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="10dbc-104">Methods</span></span>  
  
|<span data-ttu-id="10dbc-105">Método</span><span class="sxs-lookup"><span data-stu-id="10dbc-105">Method</span></span>|<span data-ttu-id="10dbc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="10dbc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10dbc-107">Método clone</span><span class="sxs-lookup"><span data-stu-id="10dbc-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="10dbc-108">Obtém um ponteiro de interface para uma cópia deste `ICorProfilerModuleEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="10dbc-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="10dbc-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="10dbc-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="10dbc-110">Obtém o número de módulos gerenciados que foram carregados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10dbc-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="10dbc-111">Próximo método</span><span class="sxs-lookup"><span data-stu-id="10dbc-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="10dbc-112">Obtém o número especificado de contíguos módulos de uma coleção sequencial de objetos, a posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="10dbc-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="10dbc-113">Método Reset</span><span class="sxs-lookup"><span data-stu-id="10dbc-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="10dbc-114">Move o cursor do enumerador para a posição inicial da sequência de.</span><span class="sxs-lookup"><span data-stu-id="10dbc-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="10dbc-115">Método Skip</span><span class="sxs-lookup"><span data-stu-id="10dbc-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="10dbc-116">Avança a posição do cursor do enumerador para que o número especificado de elementos será ignorado.</span><span class="sxs-lookup"><span data-stu-id="10dbc-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10dbc-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="10dbc-117">Remarks</span></span>  
 <span data-ttu-id="10dbc-118">O `ICorProfilerModuleEnum` interface é um enumerador.</span><span class="sxs-lookup"><span data-stu-id="10dbc-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="10dbc-119">Ele permite que o destinatário de uma matriz para elementos de pull do remetente a uma taxa que é apropriado para o receptor.</span><span class="sxs-lookup"><span data-stu-id="10dbc-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="10dbc-120">Em outras palavras, o destinatário é capaz de controlar explicitamente o fluxo de elementos da matriz, evitando, assim, os problemas associados à transmitindo matrizes grandes como parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="10dbc-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10dbc-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10dbc-121">Requirements</span></span>  
 <span data-ttu-id="10dbc-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10dbc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10dbc-123">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10dbc-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10dbc-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10dbc-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10dbc-125">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10dbc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10dbc-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10dbc-126">See Also</span></span>  
 [<span data-ttu-id="10dbc-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="10dbc-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="10dbc-128">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="10dbc-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="10dbc-129">Método EnumModules</span><span class="sxs-lookup"><span data-stu-id="10dbc-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
