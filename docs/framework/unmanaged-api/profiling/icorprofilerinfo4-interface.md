---
title: Interface ICorProfilerInfo4
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f452a3324365fb23e1affc11dbdb2ede15346010
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462436"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="af0de-102">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="af0de-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="af0de-103">Fornece métodos que criadores de perfil de código usam para se comunicar com o common language runtime (CLR) para controlar o monitoramento de eventos e informações de solicitação.</span><span class="sxs-lookup"><span data-stu-id="af0de-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="af0de-104">.</span><span class="sxs-lookup"><span data-stu-id="af0de-104">.</span></span> <span data-ttu-id="af0de-105">O `ICorProfilerInfo4` interface é uma extensão do outro `ICorProfilerInfo` interfaces.</span><span class="sxs-lookup"><span data-stu-id="af0de-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="af0de-106">Ele fornece novos métodos para dar suporte a recompilação just-in-time (JIT), adicionada no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af0de-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af0de-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="af0de-107">Methods</span></span>  
  
|<span data-ttu-id="af0de-108">Método</span><span class="sxs-lookup"><span data-stu-id="af0de-108">Method</span></span>|<span data-ttu-id="af0de-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="af0de-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af0de-110">Método EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="af0de-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="af0de-111">Retorna um enumerador para todas as funções que foram anteriormente compilados JIT e recompilado JIT.</span><span class="sxs-lookup"><span data-stu-id="af0de-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="af0de-112">Método EnumThreads</span><span class="sxs-lookup"><span data-stu-id="af0de-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="af0de-113">Obtém um enumerador que fornece métodos para sequencialmente iterar através da coleção de todos os threads gerenciados no processo com perfil.</span><span class="sxs-lookup"><span data-stu-id="af0de-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="af0de-114">Método GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="af0de-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="af0de-115">Obtém as extensões de código nativo associado com a versão recompilada JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="af0de-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="af0de-116">Método GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="af0de-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="af0de-117">Um ponteiro de instrução do código gerenciado é mapeado para a versão recompilada JIT de uma função especificada.</span><span class="sxs-lookup"><span data-stu-id="af0de-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="af0de-118">Método GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="af0de-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="af0de-119">Obtém um mapa do Microsoft intermediate language (MSIL) desloca para deslocamentos nativo para o código contido na versão recompilada JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="af0de-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="af0de-120">Método GetObjectSize2</span><span class="sxs-lookup"><span data-stu-id="af0de-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="af0de-121">Retorna o tamanho de um objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="af0de-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="af0de-122">Método GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="af0de-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="af0de-123">Retorna uma matriz de IDs de identificar todos os recompilado JIT versões da função especificada ainda alocados.</span><span class="sxs-lookup"><span data-stu-id="af0de-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="af0de-124">Método InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="af0de-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="af0de-125">Inicializa o thread atual antes de criador de perfil subsequente chamadas à API no mesmo thread, portanto esse deadlock pode ser evitado.</span><span class="sxs-lookup"><span data-stu-id="af0de-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="af0de-126">Método RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="af0de-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="af0de-127">Solicita uma recompilação de JIT de todas as instâncias das funções especificadas.</span><span class="sxs-lookup"><span data-stu-id="af0de-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="af0de-128">Método RequestRevert</span><span class="sxs-lookup"><span data-stu-id="af0de-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="af0de-129">Reverte todas as instâncias das funções especificadas para suas versões originais.</span><span class="sxs-lookup"><span data-stu-id="af0de-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af0de-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="af0de-130">Remarks</span></span>  
 <span data-ttu-id="af0de-131">O CLR implementa os métodos do `ICorProfilerInfo4` interface usando o modelo de segmentação livre.</span><span class="sxs-lookup"><span data-stu-id="af0de-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="af0de-132">Cada método retorna um HRESULT indicando êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="af0de-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="af0de-133">Para obter uma lista de possíveis códigos de retorno, consulte o arquivo corerror.</span><span class="sxs-lookup"><span data-stu-id="af0de-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af0de-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af0de-134">Requirements</span></span>  
 <span data-ttu-id="af0de-135">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af0de-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af0de-136">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af0de-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af0de-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af0de-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af0de-138">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af0de-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af0de-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af0de-139">See Also</span></span>  
 [<span data-ttu-id="af0de-140">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="af0de-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="af0de-141">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="af0de-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
