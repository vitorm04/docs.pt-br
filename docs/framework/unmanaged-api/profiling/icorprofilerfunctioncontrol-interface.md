---
title: Interface ICorProfilerFunctionControl
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl
helpviewer_keywords: ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09a0a839c9cd69c7926c19cceffc56ee928f2f02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="5225b-102">Interface ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="5225b-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="5225b-103">Fornece métodos que permitem a um criador de perfis de código se comunicar com o tempo de execução de linguagem comum (CLR) para controlar como o compilador JIT deve gerar código ao recompilar um método específico.</span><span class="sxs-lookup"><span data-stu-id="5225b-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5225b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5225b-104">Methods</span></span>  
  
|<span data-ttu-id="5225b-105">Método</span><span class="sxs-lookup"><span data-stu-id="5225b-105">Method</span></span>|<span data-ttu-id="5225b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5225b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5225b-107">Método SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="5225b-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="5225b-108">Define um ou mais sinalizadores do [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) função recompilação de enumeração para controlar a geração de código para um just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="5225b-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="5225b-109">Método SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="5225b-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="5225b-110">Substitui o corpo CIL (Common Intermediate Language) do método.</span><span class="sxs-lookup"><span data-stu-id="5225b-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="5225b-111">Método SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="5225b-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="5225b-112">Define um mapa de códigos para a função especificada usando as entradas de mapa Common Intermediate Language (CIL) especificadas.</span><span class="sxs-lookup"><span data-stu-id="5225b-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5225b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="5225b-113">Remarks</span></span>  
 <span data-ttu-id="5225b-114">A interface de `ICorProfilerFunctionControl` fornece métodos para controlar a geração de código para uma única função recompilada.</span><span class="sxs-lookup"><span data-stu-id="5225b-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="5225b-115">O criador de perfil obtém uma instância desta interface por meio de [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="5225b-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="5225b-116">Cada instância do `ICorProfilerFunctionControl` controla todas as instâncias de uma função.</span><span class="sxs-lookup"><span data-stu-id="5225b-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5225b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5225b-117">Requirements</span></span>  
 <span data-ttu-id="5225b-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5225b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5225b-119">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5225b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5225b-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5225b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5225b-121">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5225b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5225b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5225b-122">See Also</span></span>  
 [<span data-ttu-id="5225b-123">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="5225b-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="5225b-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5225b-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5225b-125">Método EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="5225b-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
