---
title: Função StackSnapshotCallback
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427070"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="7ffd7-102">Função StackSnapshotCallback</span><span class="sxs-lookup"><span data-stu-id="7ffd7-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="7ffd7-103">Fornece ao criador de perfil informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante uma movimentação de pilha, que é iniciada pelo método [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ffd7-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ffd7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ffd7-104">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ffd7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ffd7-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="7ffd7-106">no Se esse valor for zero, esse retorno de chamada será para uma execução de quadros não gerenciados; caso contrário, é o identificador de uma função gerenciada e esse retorno de chamada é para um quadro gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="7ffd7-107">no O valor do ponteiro de instrução de código nativo no quadro.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="7ffd7-108">no Um valor `COR_PRF_FRAME_INFO` que faz referência a informações sobre o registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="7ffd7-109">Esse valor é válido para uso somente durante este retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7ffd7-110">no O tamanho da estrutura de `CONTEXT`, que é referenciada pelo parâmetro `context`.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="7ffd7-111">no Um ponteiro para uma estrutura de `CONTEXT` Win32 que representa o estado da CPU para esse quadro.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="7ffd7-112">O parâmetro `context` será válido somente se o sinalizador de COR_PRF_SNAPSHOT_CONTEXT foi passado em `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="7ffd7-113">no Um ponteiro para os dados do cliente, que é passado diretamente por meio de `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ffd7-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ffd7-114">Remarks</span></span>  
 <span data-ttu-id="7ffd7-115">A função `StackSnapshotCallback` é implementada pelo gravador do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="7ffd7-116">Você deve limitar a complexidade do trabalho feito em `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="7ffd7-117">Por exemplo, ao usar `ICorProfilerInfo2::DoStackSnapshot` de maneira assíncrona, o thread de destino pode estar mantendo bloqueios.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="7ffd7-118">Se o código dentro de `StackSnapshotCallback` exigir os mesmos bloqueios, um deadlock poderá acontecer.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="7ffd7-119">O método `ICorProfilerInfo2::DoStackSnapshot` chama a função `StackSnapshotCallback` uma vez por quadro gerenciado ou uma vez por execução de quadros não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="7ffd7-120">Se `StackSnapshotCallback` for chamado para uma execução de quadros não gerenciados, o criador de perfil poderá usar o contexto de registro (referenciado pelo parâmetro `context`) para executar sua própria movimentação de pilha não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="7ffd7-121">Nesse caso, a estrutura de `CONTEXT` do Win32 representa o estado da CPU para o quadro enviado mais recentemente dentro da execução de quadros não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="7ffd7-122">Embora a estrutura de `CONTEXT` do Win32 inclua valores para todos os registros, você deve confiar apenas nos valores do registro de ponteiro de pilha, registro de ponteiro de quadro, registro de ponteiro de instrução e os registros de inteiros não voláteis (ou seja, preservados).</span><span class="sxs-lookup"><span data-stu-id="7ffd7-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ffd7-123">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7ffd7-123">Requirements</span></span>  
 <span data-ttu-id="7ffd7-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ffd7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ffd7-125">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="7ffd7-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7ffd7-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ffd7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ffd7-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ffd7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ffd7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ffd7-128">See also</span></span>

- [<span data-ttu-id="7ffd7-129">Método DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="7ffd7-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="7ffd7-130">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="7ffd7-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
