---
title: Função FunctionEnter3
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: b435e1a3504dd623421f977ffc48264f8b0dcb5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500696"
---
# <a name="functionenter3-function"></a><span data-ttu-id="a3a99-102">Função FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a3a99-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="a3a99-103">Notifica o criador de perfil que o controle está sendo passado para uma função.</span><span class="sxs-lookup"><span data-stu-id="a3a99-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a99-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3a99-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3a99-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3a99-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="a3a99-106">\[in] o identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="a3a99-106">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3a99-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3a99-107">Remarks</span></span>  
 <span data-ttu-id="a3a99-108">A `FunctionEnter3` função de retorno de chamada notifica o criador de perfil conforme as funções estão sendo chamadas, mas não dá suporte à inspeção de argumento.</span><span class="sxs-lookup"><span data-stu-id="a3a99-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="a3a99-109">Use o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="a3a99-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a3a99-110">A `FunctionEnter3` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="a3a99-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="a3a99-111">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="a3a99-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a3a99-112">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="a3a99-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a3a99-113">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="a3a99-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a3a99-114">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="a3a99-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3a99-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3a99-115">Requirements</span></span>  
 <span data-ttu-id="a3a99-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3a99-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3a99-117">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="a3a99-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a3a99-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3a99-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3a99-119">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3a99-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a99-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="a3a99-120">See also</span></span>

- [<span data-ttu-id="a3a99-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a3a99-121">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="a3a99-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a3a99-122">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="a3a99-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a3a99-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="a3a99-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a3a99-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a3a99-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a3a99-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a3a99-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a3a99-126">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="a3a99-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a3a99-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a3a99-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a3a99-128">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a3a99-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="a3a99-129">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a3a99-130">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="a3a99-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
