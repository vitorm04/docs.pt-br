---
title: "Método ICorProfilerFunctionControl::SetCodegenFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetCodegenFlags
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eb212b0fb777e960d7121dadaf4715b44306db6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="7eccc-102">Método ICorProfilerFunctionControl::SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="7eccc-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="7eccc-103">Define um ou mais sinalizadores do [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) função recompilação de enumeração para controlar a geração de código para um just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="7eccc-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eccc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7eccc-104">Syntax</span></span>  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7eccc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7eccc-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="7eccc-106">[in] Um ou mais sinalizadores do [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="7eccc-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eccc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7eccc-107">Remarks</span></span>  
 <span data-ttu-id="7eccc-108">O criador de perfil obtém uma instância desta interface por meio de [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7eccc-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="7eccc-109">`SetCodegenFlags`permite que o criador de perfil controlar a geração de código para a função recompilada.</span><span class="sxs-lookup"><span data-stu-id="7eccc-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="7eccc-110">Assim como acontece com todos os outros parâmetros de recompilação JIT, os sinalizadores de geração de código se aplicam a todas as instâncias da função.</span><span class="sxs-lookup"><span data-stu-id="7eccc-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="7eccc-111">O compilador JIT considera esses sinalizadores de compilação, juntamente com outros sinalizadores especificados por outras fontes, durante a compilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="7eccc-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="7eccc-112">Outras fontes incluem o depurador, sinalizadores globais definidas pelo criador de perfil na inicialização, usando o [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método (com os valores `COR_PRF_DISABLE_INLINING` e `COR_PRF_DISABLE_OPTIMIZATIONS`) e o criador de perfil [ : Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7eccc-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="7eccc-113">O compilador JIT dá prioridade a uma fonte que solicita o mínimo de otimização.</span><span class="sxs-lookup"><span data-stu-id="7eccc-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="7eccc-114">Por exemplo, se o criador de perfil especifica `COR_PRF_DISABLE_INLINING` na inicialização, mas não especifica `COR_PRF_CODEGEN_DISABLE_INLINING` no [: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) retorno de chamada, inlining ainda está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="7eccc-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="7eccc-115">Da mesma forma, se o criador de perfil não especificar `COR_PRF_CODEGEN_DISABLE_INLINING` na `SetCodegenFlags`, mas, em seguida, desabilita inlining usando o [: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) retorno de chamada, inlining está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="7eccc-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eccc-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7eccc-116">Requirements</span></span>  
 <span data-ttu-id="7eccc-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eccc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eccc-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7eccc-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7eccc-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eccc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eccc-120">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eccc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eccc-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7eccc-121">See Also</span></span>  
 [<span data-ttu-id="7eccc-122">Interface ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="7eccc-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
