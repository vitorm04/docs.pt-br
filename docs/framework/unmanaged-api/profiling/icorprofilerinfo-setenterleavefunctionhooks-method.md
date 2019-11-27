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
ms.openlocfilehash: 45593e7e30e1c8f8036489936aab3c607b01dd52
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438653"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="eeaf0-102">Método ICorProfilerInfo::SetEnterLeaveFunctionHooks</span><span class="sxs-lookup"><span data-stu-id="eeaf0-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="eeaf0-103">Especifica funções implementadas pelo Profiler a serem chamadas em "Inserir", "deixar" e "tailcall" ganchos de funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="eeaf0-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeaf0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eeaf0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eeaf0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eeaf0-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="eeaf0-106">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="eeaf0-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="eeaf0-107">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="eeaf0-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="eeaf0-108">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="eeaf0-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eeaf0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="eeaf0-109">Remarks</span></span>  
 <span data-ttu-id="eeaf0-110">No .NET Framework versão 1,0, cada ponteiro de função pode ser nulo para desabilitar esse retorno de chamada correspondente.</span><span class="sxs-lookup"><span data-stu-id="eeaf0-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="eeaf0-111">Somente um conjunto de retornos de chamada pode estar ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="eeaf0-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="eeaf0-112">Portanto, se um criador de perfil chamar `SetEnterLeaveFunctionHooks` e [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` terá precedência.</span><span class="sxs-lookup"><span data-stu-id="eeaf0-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="eeaf0-113">O método `SetEnterLeaveFunctionHooks` pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="eeaf0-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeaf0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eeaf0-114">Requirements</span></span>  
 <span data-ttu-id="eeaf0-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeaf0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeaf0-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eeaf0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eeaf0-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eeaf0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eeaf0-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeaf0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeaf0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eeaf0-119">See also</span></span>

- [<span data-ttu-id="eeaf0-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="eeaf0-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
