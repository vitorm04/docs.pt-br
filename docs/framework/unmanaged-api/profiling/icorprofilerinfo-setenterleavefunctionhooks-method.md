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
ms.openlocfilehash: f7bc1954d11134a4515d2e29e9e0eb1626ae5d26
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863421"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="b6392-102">Método ICorProfilerInfo::SetEnterLeaveFunctionHooks</span><span class="sxs-lookup"><span data-stu-id="b6392-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="b6392-103">Especifica funções implementadas pelo Profiler a serem chamadas em "Inserir", "deixar" e "tailcall" ganchos de funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="b6392-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6392-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6392-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6392-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b6392-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="b6392-106">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionEnter](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b6392-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="b6392-107">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionLeave](functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b6392-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="b6392-108">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionTailcall](functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b6392-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6392-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6392-109">Remarks</span></span>  
 <span data-ttu-id="b6392-110">No .NET Framework versão 1,0, cada ponteiro de função pode ser nulo para desabilitar esse retorno de chamada correspondente.</span><span class="sxs-lookup"><span data-stu-id="b6392-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="b6392-111">Somente um conjunto de retornos de chamada pode estar ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="b6392-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="b6392-112">Portanto, se um criador de perfil chamar `SetEnterLeaveFunctionHooks` e [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` terá precedência.</span><span class="sxs-lookup"><span data-stu-id="b6392-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="b6392-113">O método `SetEnterLeaveFunctionHooks` pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="b6392-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6392-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b6392-114">Requirements</span></span>  
 <span data-ttu-id="b6392-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6392-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6392-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b6392-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6392-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6392-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6392-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6392-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6392-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="b6392-119">See also</span></span>

- [<span data-ttu-id="b6392-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b6392-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
