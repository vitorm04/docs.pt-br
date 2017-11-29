---
title: Interface ICorProfilerInfo4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db91347ad2c951c28ea7b653336450929d37bdcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="bcd32-102">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="bcd32-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="bcd32-103">Fornece métodos que criadores de perfil de código usam para se comunicar com o common language runtime (CLR) para controlar o monitoramento de eventos e informações de solicitação.</span><span class="sxs-lookup"><span data-stu-id="bcd32-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="bcd32-104">.</span><span class="sxs-lookup"><span data-stu-id="bcd32-104">.</span></span> <span data-ttu-id="bcd32-105">O `ICorProfilerInfo4` interface é uma extensão do outro `ICorProfilerInfo` interfaces.</span><span class="sxs-lookup"><span data-stu-id="bcd32-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="bcd32-106">Ele fornece novos métodos para dar suporte a recompilação just-in-time (JIT), adicionada no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bcd32-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bcd32-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="bcd32-107">Methods</span></span>  
  
|<span data-ttu-id="bcd32-108">Método</span><span class="sxs-lookup"><span data-stu-id="bcd32-108">Method</span></span>|<span data-ttu-id="bcd32-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcd32-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bcd32-110">Método EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="bcd32-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="bcd32-111">Retorna um enumerador para todas as funções que foram anteriormente compilados JIT e recompilado JIT.</span><span class="sxs-lookup"><span data-stu-id="bcd32-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="bcd32-112">Método EnumThreads</span><span class="sxs-lookup"><span data-stu-id="bcd32-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="bcd32-113">Obtém um enumerador que fornece métodos para sequencialmente iterar através da coleção de todos os threads gerenciados no processo com perfil.</span><span class="sxs-lookup"><span data-stu-id="bcd32-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="bcd32-114">Método GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="bcd32-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="bcd32-115">Obtém as extensões de código nativo associado com a versão recompilada JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="bcd32-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="bcd32-116">Método GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="bcd32-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="bcd32-117">Um ponteiro de instrução do código gerenciado é mapeado para a versão recompilada JIT de uma função especificada.</span><span class="sxs-lookup"><span data-stu-id="bcd32-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="bcd32-118">Método GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="bcd32-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="bcd32-119">Obtém um mapa do Microsoft intermediate language (MSIL) desloca para deslocamentos nativo para o código contido na versão recompilada JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="bcd32-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="bcd32-120">Método GetObjectSize2</span><span class="sxs-lookup"><span data-stu-id="bcd32-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="bcd32-121">Retorna o tamanho de um objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="bcd32-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="bcd32-122">Método GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="bcd32-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="bcd32-123">Retorna uma matriz de IDs de identificar todos os recompilado JIT versões da função especificada ainda alocados.</span><span class="sxs-lookup"><span data-stu-id="bcd32-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="bcd32-124">Método InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="bcd32-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="bcd32-125">Inicializa o thread atual antes de criador de perfil subsequente chamadas à API no mesmo thread, portanto esse deadlock pode ser evitado.</span><span class="sxs-lookup"><span data-stu-id="bcd32-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="bcd32-126">Método RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="bcd32-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="bcd32-127">Solicita uma recompilação de JIT de todas as instâncias das funções especificadas.</span><span class="sxs-lookup"><span data-stu-id="bcd32-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="bcd32-128">Método RequestRevert</span><span class="sxs-lookup"><span data-stu-id="bcd32-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="bcd32-129">Reverte todas as instâncias das funções especificadas para suas versões originais.</span><span class="sxs-lookup"><span data-stu-id="bcd32-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcd32-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="bcd32-130">Remarks</span></span>  
 <span data-ttu-id="bcd32-131">O CLR implementa os métodos do `ICorProfilerInfo4` interface usando o modelo de segmentação livre.</span><span class="sxs-lookup"><span data-stu-id="bcd32-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="bcd32-132">Cada método retorna um HRESULT indicando êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="bcd32-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="bcd32-133">Para obter uma lista de possíveis códigos de retorno, consulte o arquivo corerror.</span><span class="sxs-lookup"><span data-stu-id="bcd32-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcd32-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bcd32-134">Requirements</span></span>  
 <span data-ttu-id="bcd32-135">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcd32-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcd32-136">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bcd32-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bcd32-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcd32-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcd32-138">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcd32-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd32-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bcd32-139">See Also</span></span>  
 [<span data-ttu-id="bcd32-140">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="bcd32-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="bcd32-141">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="bcd32-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
