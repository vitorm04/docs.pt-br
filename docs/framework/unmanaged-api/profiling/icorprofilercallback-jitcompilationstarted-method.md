---
title: Método ICorProfilerCallback::JITCompilationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 57981ef134dc3f30337d47f5cee426a25d0414cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500033"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="c775b-102">Método ICorProfilerCallback::JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="c775b-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="c775b-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) começou a compilar uma função.</span><span class="sxs-lookup"><span data-stu-id="c775b-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c775b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c775b-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c775b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c775b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c775b-106">no A ID da função para a qual a compilação está sendo iniciada.</span><span class="sxs-lookup"><span data-stu-id="c775b-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="c775b-107">no Um valor que indica ao criador de perfil se o bloqueio afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c775b-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="c775b-108">O valor é `true` se o bloqueio pode fazer com que o tempo de execução aguarde o thread de chamada retornar desse retorno de chamada; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="c775b-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="c775b-109">Embora um valor de `true` não danifique o tempo de execução, ele pode distorcer os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="c775b-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c775b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c775b-110">Remarks</span></span>  
 <span data-ttu-id="c775b-111">É possível receber mais de um par de `JITCompilationStarted` chamadas e [ICorProfilerCallback:: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) para cada função devido à maneira como o tempo de execução manipula construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="c775b-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="c775b-112">Por exemplo, o tempo de execução inicia o método A de compilação JIT a, mas o construtor de classe para a classe B precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="c775b-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="c775b-113">Portanto, o tempo de execução JIT compila o construtor para a classe B e o executa.</span><span class="sxs-lookup"><span data-stu-id="c775b-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="c775b-114">Enquanto o Construtor está em execução, ele faz uma chamada para o método A, o que faz com que o método A seja compilado em JIT novamente.</span><span class="sxs-lookup"><span data-stu-id="c775b-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="c775b-115">Nesse cenário, a primeira compilação JIT do método A é interrompida.</span><span class="sxs-lookup"><span data-stu-id="c775b-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="c775b-116">No entanto, ambas as tentativas de compilação JIT do método A são relatadas com eventos de compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="c775b-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="c775b-117">Se o criador de perfil substituir o código MSIL (Microsoft Intermediate Language) para o método A chamando o método [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) , ele deverá fazer isso para ambos os `JITCompilationStarted` eventos, mas poderá usar o mesmo bloco MSIL para ambos.</span><span class="sxs-lookup"><span data-stu-id="c775b-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="c775b-118">Os profileres devem dar suporte à sequência de retornos de chamada JIT nos casos em que dois threads estão realizando retornos de chamada simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="c775b-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="c775b-119">Por exemplo, thread A chama `JITCompilationStarted` .</span><span class="sxs-lookup"><span data-stu-id="c775b-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="c775b-120">No entanto, antes de chamar Thread A `JITCompilationFinished` , thread B chama [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função do retorno de chamada do thread A `JITCompilationStarted` .</span><span class="sxs-lookup"><span data-stu-id="c775b-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="c775b-121">Pode parecer que a ID da função ainda não deve ser válida porque uma chamada para `JITCompilationFinished` ainda não foi recebida pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="c775b-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="c775b-122">No entanto, em um caso como este, a ID da função é válida.</span><span class="sxs-lookup"><span data-stu-id="c775b-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c775b-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c775b-123">Requirements</span></span>  
 <span data-ttu-id="c775b-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c775b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c775b-125">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c775b-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c775b-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c775b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c775b-127">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c775b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c775b-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="c775b-128">See also</span></span>

- [<span data-ttu-id="c775b-129">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c775b-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c775b-130">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="c775b-130">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
