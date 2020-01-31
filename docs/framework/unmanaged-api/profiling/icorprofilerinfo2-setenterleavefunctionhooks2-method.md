---
title: Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868571"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="de1e5-102">Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="de1e5-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="de1e5-103">Especifica as funções implementadas pelo Profiler a serem chamadas nas versões atualizadas dos ganchos "Enter", "sair" e "tailcall" das funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="de1e5-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de1e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de1e5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de1e5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de1e5-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="de1e5-106">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="de1e5-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="de1e5-107">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionLeave2](functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="de1e5-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="de1e5-108">no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionTailcall2](functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="de1e5-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de1e5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="de1e5-109">Remarks</span></span>  
 <span data-ttu-id="de1e5-110">O método `SetEnterLeaveFunctionHooks2` é semelhante ao método [ICorProfilerInfo:: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de1e5-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="de1e5-111">Use o primeiro para especificar funções a serem usadas como versões mais recentes dos retornos de chamada enter/leave/tailcall e a última para especificar as funções a serem usadas como versões mais antigas dos retornos de chamada enter/leave/tailcall.</span><span class="sxs-lookup"><span data-stu-id="de1e5-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="de1e5-112">Somente um conjunto de retornos de chamada pode estar ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="de1e5-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="de1e5-113">Portanto, se um criador de perfil chamar `ICorProfilerInfo::SetEnterLeaveFunctionHooks` e `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` será usado.</span><span class="sxs-lookup"><span data-stu-id="de1e5-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="de1e5-114">O método `SetEnterLeaveFunctionHooks2` pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="de1e5-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de1e5-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="de1e5-115">Requirements</span></span>  
 <span data-ttu-id="de1e5-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de1e5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de1e5-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="de1e5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de1e5-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de1e5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de1e5-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de1e5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1e5-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="de1e5-120">See also</span></span>

- [<span data-ttu-id="de1e5-121">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="de1e5-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="de1e5-122">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="de1e5-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
