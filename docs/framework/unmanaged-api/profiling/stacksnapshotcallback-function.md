---
title: "Função StackSnapshotCallback"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackSnapshotCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: StackSnapshotCallback
helpviewer_keywords: StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 92f7071ebcf7664b3622c180b9f1bade50909cea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="b4447-102">Função StackSnapshotCallback</span><span class="sxs-lookup"><span data-stu-id="b4447-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="b4447-103">Fornece o criador de perfil com informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante um exame da pilha, que é iniciado com a [Icorprofilerinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b4447-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4447-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4447-104">Syntax</span></span>  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4447-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4447-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="b4447-106">[in] Se esse valor for zero, esse retorno de chamada é para uma execução de quadros não gerenciados; Caso contrário, o identificador de uma função gerenciada e esse retorno de chamada é para um quadro gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b4447-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="b4447-107">[in] O valor do ponteiro de instrução do código nativo no quadro.</span><span class="sxs-lookup"><span data-stu-id="b4447-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="b4447-108">[in] Um `COR_PRF_FRAME_INFO` valor que faz referência a informações sobre o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="b4447-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="b4447-109">Esse valor é válido para uso somente durante esse retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b4447-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b4447-110">[in] O tamanho do `CONTEXT` estrutura, que é referenciada pelo `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b4447-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="b4447-111">[in] Um ponteiro para um Win32 `CONTEXT` estrutura que representa o estado da CPU por este quadro.</span><span class="sxs-lookup"><span data-stu-id="b4447-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="b4447-112">O `context` parâmetro é válido somente se o sinalizador COR_PRF_SNAPSHOT_CONTEXT foi passado `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="b4447-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="b4447-113">[in] Um ponteiro para os dados do cliente, que são passados diretamente por meio da `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="b4447-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4447-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4447-114">Remarks</span></span>  
 <span data-ttu-id="b4447-115">O `StackSnapshotCallback` função é implementada pelo gerador de criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="b4447-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="b4447-116">Você deve limitar a complexidade do trabalho no `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="b4447-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="b4447-117">Por exemplo, ao usar `ICorProfilerInfo2::DoStackSnapshot` de maneira assíncrona, o thread de destino pode ser mantendo bloqueios.</span><span class="sxs-lookup"><span data-stu-id="b4447-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="b4447-118">Se código dentro de `StackSnapshotCallback` requer os mesmos bloqueios, poderia causar um deadlock.</span><span class="sxs-lookup"><span data-stu-id="b4447-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="b4447-119">O `ICorProfilerInfo2::DoStackSnapshot` chamadas de método de `StackSnapshotCallback` função uma vez por quadro gerenciado ou de uma vez por execução de quadros não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b4447-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="b4447-120">Se `StackSnapshotCallback` é chamado para uma execução de quadros não gerenciados, o criador de perfil pode usar o contexto de registro (referenciado pelo `context` parâmetro) para executar seu próprios não gerenciados na pilha.</span><span class="sxs-lookup"><span data-stu-id="b4447-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="b4447-121">Nesse caso, o Win32 `CONTEXT` estrutura representa o estado da CPU para o quadro enviado mais recentemente dentro da execução de quadros não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b4447-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="b4447-122">Embora o Win32 `CONTEXT` estrutura inclui valores para todos os registros, você deve depender apenas os valores do registro de ponteiro de pilha, registro de ponteiro de quadro, registro de ponteiro de instrução e não-volátil (que é, preservado) registra inteiro.</span><span class="sxs-lookup"><span data-stu-id="b4447-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4447-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4447-123">Requirements</span></span>  
 <span data-ttu-id="b4447-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4447-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4447-125">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="b4447-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b4447-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4447-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4447-127">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4447-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4447-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4447-128">See Also</span></span>  
 [<span data-ttu-id="b4447-129">Método DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="b4447-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="b4447-130">Funções estáticas globais de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b4447-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
