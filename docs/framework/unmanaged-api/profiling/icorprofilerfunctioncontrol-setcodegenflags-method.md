---
title: Método ICorProfilerFunctionControl::SetCodegenFlags
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
ms.openlocfilehash: 75414ec3d2b30fe8afc5db1e97c81f34b29a3115
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864668"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="8068f-102">Método ICorProfilerFunctionControl::SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="8068f-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="8068f-103">Define um ou mais sinalizadores da enumeração de [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) para controlar a geração de código para uma função recompilada JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="8068f-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8068f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8068f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8068f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8068f-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="8068f-106">no Um ou mais sinalizadores da enumeração de [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="8068f-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8068f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8068f-107">Remarks</span></span>  
 <span data-ttu-id="8068f-108">O criador de perfil Obtém uma instância dessa interface por meio do retorno de chamada [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8068f-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="8068f-109">`SetCodegenFlags` permite que o criador de perfil controle a geração de código para a função recompilada.</span><span class="sxs-lookup"><span data-stu-id="8068f-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="8068f-110">Assim como acontece com todos os outros parâmetros de recompilação JIT, os sinalizadores de geração de código se aplicam a todas as instâncias da função.</span><span class="sxs-lookup"><span data-stu-id="8068f-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="8068f-111">O compilador JIT considera esses sinalizadores de compilação, juntamente com outros sinalizadores especificados por outras fontes, ao compilar uma função.</span><span class="sxs-lookup"><span data-stu-id="8068f-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="8068f-112">As outras fontes incluem o depurador, os sinalizadores globais definidos pelo criador de perfil na inicialização usando o método [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) (com os valores `COR_PRF_DISABLE_INLINING` e `COR_PRF_DISABLE_OPTIMIZATIONS`) e o retorno de chamada [ICorProfilerCallback:: JITInlining](icorprofilercallback-jitinlining-method.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="8068f-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="8068f-113">O compilador JIT dá precedência a uma fonte que solicita a menor quantidade de otimização.</span><span class="sxs-lookup"><span data-stu-id="8068f-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="8068f-114">Por exemplo, se o criador de perfil especificar `COR_PRF_DISABLE_INLINING` na inicialização, mas não especificar `COR_PRF_CODEGEN_DISABLE_INLINING` no retorno de chamada [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) , o inlining ainda estará desabilitado.</span><span class="sxs-lookup"><span data-stu-id="8068f-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="8068f-115">Da mesma forma, se o criador de perfil não especificar `COR_PRF_CODEGEN_DISABLE_INLINING` em `SetCodegenFlags`, mas, em seguida, desabilitar o inalinhamento usando o retorno de chamada [ICorProfilerCallback:: JITInlining](icorprofilercallback-jitinlining-method.md) , o inalinhamento será desabilitado.</span><span class="sxs-lookup"><span data-stu-id="8068f-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8068f-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="8068f-116">Requirements</span></span>  
 <span data-ttu-id="8068f-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8068f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8068f-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8068f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8068f-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8068f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8068f-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8068f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8068f-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="8068f-121">See also</span></span>

- [<span data-ttu-id="8068f-122">Interface ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="8068f-122">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
