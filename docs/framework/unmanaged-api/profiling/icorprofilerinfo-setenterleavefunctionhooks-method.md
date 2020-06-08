---
title: Método ICorProfilerInfo::SetEnterLeaveFunctionHooks
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: cf0726a12b0274fd7a38e82b66c33430d26b031a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497446"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="fb141-102">Método ICorProfilerInfo::SetEnterLeaveFunctionHooks</span><span class="sxs-lookup"><span data-stu-id="fb141-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="fb141-103">Especifica funções implementadas pelo Profiler a serem chamadas em "Inserir", "deixar" e "tailcall" ganchos de funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="fb141-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb141-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb141-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb141-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb141-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="fb141-106">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionEnter](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="fb141-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="fb141-107">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionLeave](functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="fb141-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="fb141-108">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionTailcall](functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="fb141-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb141-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb141-109">Remarks</span></span>  
 <span data-ttu-id="fb141-110">No .NET Framework versão 1,0, cada ponteiro de função pode ser nulo para desabilitar esse retorno de chamada correspondente.</span><span class="sxs-lookup"><span data-stu-id="fb141-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="fb141-111">Somente um conjunto de retornos de chamada pode estar ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="fb141-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="fb141-112">Assim, se um criador de perfil `SetEnterLeaveFunctionHooks` chamar [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` terá precedência.</span><span class="sxs-lookup"><span data-stu-id="fb141-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="fb141-113">O `SetEnterLeaveFunctionHooks` método pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="fb141-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb141-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb141-114">Requirements</span></span>  
 <span data-ttu-id="fb141-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb141-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb141-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fb141-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb141-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb141-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb141-118">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb141-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb141-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb141-119">See also</span></span>

- [<span data-ttu-id="fb141-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="fb141-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
