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
ms.openlocfilehash: 27cce8a77d4236829124b45650d5d0ac32a5150c
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49634087"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="bddcf-102">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="bddcf-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="bddcf-103">Fornece métodos que os criadores de perfil de código usam para se comunicar com o CLR (CLR) para controlar o monitoramento de eventos e informações de solicitação.</span><span class="sxs-lookup"><span data-stu-id="bddcf-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="bddcf-104">.</span><span class="sxs-lookup"><span data-stu-id="bddcf-104">.</span></span> <span data-ttu-id="bddcf-105">O `ICorProfilerInfo4` interface é uma extensão do outro `ICorProfilerInfo` interfaces.</span><span class="sxs-lookup"><span data-stu-id="bddcf-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="bddcf-106">Ele fornece novos métodos para dar suporte a recompilação de just-in-time (JIT), adicionada no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bddcf-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bddcf-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="bddcf-107">Methods</span></span>  
  
|<span data-ttu-id="bddcf-108">Método</span><span class="sxs-lookup"><span data-stu-id="bddcf-108">Method</span></span>|<span data-ttu-id="bddcf-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bddcf-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bddcf-110">Método EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="bddcf-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="bddcf-111">Retorna um enumerador para todas as funções que foram previamente compilado por JIT e recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="bddcf-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="bddcf-112">Método EnumThreads</span><span class="sxs-lookup"><span data-stu-id="bddcf-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="bddcf-113">Obtém um enumerador que fornece métodos para iterar de forma sequencial por meio da coleção de todos os threads gerenciados no processo de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="bddcf-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="bddcf-114">Método GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="bddcf-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="bddcf-115">Obtém as extensões de código nativo associado com a versão recompilado por JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="bddcf-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="bddcf-116">Método GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="bddcf-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="bddcf-117">Mapeia um ponteiro de instrução de código gerenciado para a versão recompilado por JIT de uma função especificada.</span><span class="sxs-lookup"><span data-stu-id="bddcf-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="bddcf-118">Método GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="bddcf-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="bddcf-119">Obtém um mapa da Microsoft intermediate language (MSIL) deslocamentos para deslocamentos nativos para o código contido na versão recompilado por JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="bddcf-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="bddcf-120">Método GetObjectSize2</span><span class="sxs-lookup"><span data-stu-id="bddcf-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="bddcf-121">Retorna o tamanho de um objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="bddcf-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="bddcf-122">Método GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="bddcf-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="bddcf-123">Retorna uma matriz de IDs que identificam todos os recompilado por JIT versões da função especificada que ainda são alocadas.</span><span class="sxs-lookup"><span data-stu-id="bddcf-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="bddcf-124">Método InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="bddcf-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="bddcf-125">Inicializa o thread atual com antecedência sobre o criador de perfil subsequente, chamadas de API no mesmo thread, portanto, esse deadlock pode ser evitado.</span><span class="sxs-lookup"><span data-stu-id="bddcf-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="bddcf-126">Método RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="bddcf-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="bddcf-127">Solicita uma recompilação JIT de todas as instâncias das funções especificadas.</span><span class="sxs-lookup"><span data-stu-id="bddcf-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="bddcf-128">Método RequestRevert</span><span class="sxs-lookup"><span data-stu-id="bddcf-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="bddcf-129">Reverte todas as instâncias das funções especificadas para suas versões originais.</span><span class="sxs-lookup"><span data-stu-id="bddcf-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bddcf-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="bddcf-130">Remarks</span></span>  
 <span data-ttu-id="bddcf-131">O CLR implementa os métodos do `ICorProfilerInfo4` interface usando o modelo de Threading livre.</span><span class="sxs-lookup"><span data-stu-id="bddcf-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="bddcf-132">Cada método retorna um HRESULT para indicar êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="bddcf-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="bddcf-133">Para obter uma lista dos possíveis códigos de retorno, consulte o arquivo CORERROR h.</span><span class="sxs-lookup"><span data-stu-id="bddcf-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bddcf-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bddcf-134">Requirements</span></span>  
 <span data-ttu-id="bddcf-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bddcf-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bddcf-136">**Cabeçalho:** Corprof. idl, Corprof.</span><span class="sxs-lookup"><span data-stu-id="bddcf-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bddcf-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bddcf-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bddcf-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bddcf-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bddcf-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bddcf-139">See Also</span></span>  
 [<span data-ttu-id="bddcf-140">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="bddcf-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="bddcf-141">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="bddcf-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
