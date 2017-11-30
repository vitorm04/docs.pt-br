---
title: "Método ICorProfilerCallback::JITCompilationStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a12ae3e33d5553ed99a5a26b8fc872f0d07de81e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="9aca7-102">Método ICorProfilerCallback::JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="9aca7-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="9aca7-103">Notifica o criador de perfil que o compilador just-in-time (JIT) foi iniciado compilar uma função.</span><span class="sxs-lookup"><span data-stu-id="9aca7-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aca7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9aca7-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9aca7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9aca7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9aca7-106">[in] A ID da função para a qual a compilação está iniciando.</span><span class="sxs-lookup"><span data-stu-id="9aca7-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="9aca7-107">[in] Um valor que indica o criador de perfil se bloqueio afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9aca7-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="9aca7-108">O valor é `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="9aca7-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="9aca7-109">Embora um valor de `true` não prejudicarão o tempo de execução, ele pode afetar os resultados da criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="9aca7-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aca7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9aca7-110">Remarks</span></span>  
 <span data-ttu-id="9aca7-111">É possível receber mais de um par de `JITCompilationStarted` e [Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) chama para cada função devido a maneira como o tempo de execução construtores de classe de identificadores.</span><span class="sxs-lookup"><span data-stu-id="9aca7-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="9aca7-112">Por exemplo, o tempo de execução começa a um método de compilação JIT, mas o construtor de classe para classe B deve ser executado.</span><span class="sxs-lookup"><span data-stu-id="9aca7-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="9aca7-113">Portanto, é o tempo de execução JIT compila o construtor de classe B e o executa.</span><span class="sxs-lookup"><span data-stu-id="9aca7-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="9aca7-114">Durante a execução, o construtor faz uma chamada ao método A, que faz com que o método A ser compilado por JIT novamente.</span><span class="sxs-lookup"><span data-stu-id="9aca7-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="9aca7-115">Nesse cenário, a primeira compilação JIT do método A é interrompida.</span><span class="sxs-lookup"><span data-stu-id="9aca7-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="9aca7-116">No entanto, ambas as tentativas de um método de compilação JIT são relatadas com eventos de compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="9aca7-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="9aca7-117">Se for o criador de perfil para substituir o código do Microsoft intermediate language (MSIL) para o método um chamando o [: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) método, ele deve fazer isso para ambas `JITCompilationStarted` eventos, mas ele pode usar o mesmo bloco MSIL para ambos.</span><span class="sxs-lookup"><span data-stu-id="9aca7-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="9aca7-118">Criadores de perfil devem dar suporte a sequência de retornos de chamada JIT em casos onde dois threads simultaneamente fazem retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="9aca7-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="9aca7-119">Por exemplo, um thread de chamadas `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="9aca7-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="9aca7-120">No entanto, antes de chamadas do thread A `JITCompilationFinished`, chamadas de thread B [: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função de thread do `JITCompilationStarted` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="9aca7-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="9aca7-121">Pode parecer que a ID de função não deve ainda ser válida porque uma chamada para `JITCompilationFinished` ainda não foi recebido pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="9aca7-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="9aca7-122">No entanto, em casos como esse, a ID de função é válida.</span><span class="sxs-lookup"><span data-stu-id="9aca7-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aca7-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9aca7-123">Requirements</span></span>  
 <span data-ttu-id="9aca7-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aca7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aca7-125">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9aca7-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9aca7-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9aca7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9aca7-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aca7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aca7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9aca7-128">See Also</span></span>  
 [<span data-ttu-id="9aca7-129">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9aca7-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9aca7-130">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="9aca7-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
