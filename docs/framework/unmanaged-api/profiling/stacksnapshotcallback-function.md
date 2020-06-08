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
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493975"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="4a563-102">Função StackSnapshotCallback</span><span class="sxs-lookup"><span data-stu-id="4a563-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="4a563-103">Fornece ao criador de perfil informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante uma movimentação de pilha, que é iniciada pelo método [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4a563-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a563-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a563-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4a563-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a563-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="4a563-106">no Se esse valor for zero, esse retorno de chamada será para uma execução de quadros não gerenciados; caso contrário, é o identificador de uma função gerenciada e esse retorno de chamada é para um quadro gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4a563-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="4a563-107">no O valor do ponteiro de instrução de código nativo no quadro.</span><span class="sxs-lookup"><span data-stu-id="4a563-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="4a563-108">no Um `COR_PRF_FRAME_INFO` valor que faz referência a informações sobre o registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="4a563-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="4a563-109">Esse valor é válido para uso somente durante este retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="4a563-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4a563-110">no O tamanho da `CONTEXT` estrutura, que é referenciada pelo `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4a563-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="4a563-111">no Um ponteiro para uma `CONTEXT` estrutura Win32 que representa o estado da CPU para esse quadro.</span><span class="sxs-lookup"><span data-stu-id="4a563-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="4a563-112">O `context` parâmetro será válido somente se o sinalizador de COR_PRF_SNAPSHOT_CONTEXT foi passado `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="4a563-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="4a563-113">no Um ponteiro para os dados do cliente, que são passados diretamente por meio de `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="4a563-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a563-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a563-114">Remarks</span></span>  
 <span data-ttu-id="4a563-115">A `StackSnapshotCallback` função é implementada pelo gravador do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="4a563-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="4a563-116">Você deve limitar a complexidade do trabalho feito no `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="4a563-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="4a563-117">Por exemplo, ao usar `ICorProfilerInfo2::DoStackSnapshot` de forma assíncrona, o thread de destino pode estar mantendo bloqueios.</span><span class="sxs-lookup"><span data-stu-id="4a563-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="4a563-118">Se o código dentro `StackSnapshotCallback` exigir os mesmos bloqueios, um deadlock poderia acontecer.</span><span class="sxs-lookup"><span data-stu-id="4a563-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="4a563-119">O `ICorProfilerInfo2::DoStackSnapshot` método chama a `StackSnapshotCallback` função uma vez por quadro gerenciado ou uma vez por execução de quadros não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="4a563-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="4a563-120">Se `StackSnapshotCallback` for chamado para uma execução de quadros não gerenciados, o criador de perfil poderá usar o contexto de registro (referenciado pelo `context` parâmetro) para executar sua própria movimentação de pilha não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="4a563-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="4a563-121">Nesse caso, a estrutura do Win32 `CONTEXT` representa o estado da CPU para o quadro enviado mais recentemente dentro da execução de quadros não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="4a563-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="4a563-122">Embora a `CONTEXT` estrutura Win32 inclua valores para todos os registros, você deve confiar apenas nos valores do registro de ponteiro de pilha, registro de ponteiro de quadro, registro de ponteiro de instrução e os registros inteiros não volátil (ou seja, preservados).</span><span class="sxs-lookup"><span data-stu-id="4a563-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a563-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a563-123">Requirements</span></span>  
 <span data-ttu-id="4a563-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a563-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a563-125">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="4a563-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4a563-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a563-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a563-127">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a563-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a563-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="4a563-128">See also</span></span>

- [<span data-ttu-id="4a563-129">Método DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="4a563-129">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="4a563-130">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="4a563-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
