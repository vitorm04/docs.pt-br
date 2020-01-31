---
title: Método ICorProfilerInfo3::SetFunctionIDMapper2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 107f596801832809e64088c85540c441e66189cf
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868467"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="357e1-102">Método ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="357e1-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="357e1-103">Especifica a função implementada pelo criador de perfil que será chamada para mapear valores de `FunctionID` para valores alternativos, que são passados para os ganchos de entrada/saída da função do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="357e1-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="357e1-104">Esse método estende o método [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) com um parâmetro de dados adicional, que os profileres podem usar para fazer a ambiguidade entre os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="357e1-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="357e1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="357e1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="357e1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="357e1-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="357e1-107">no Um ponteiro para uma implementação de [FunctionIDMapper2](functionidmapper2-function.md) que será chamada para mapear os valores de `FunctionID` para seus valores alternativos.</span><span class="sxs-lookup"><span data-stu-id="357e1-107">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="357e1-108">no Um ponteiro que é passado para cada chamada de função [FunctionIDMapper2](functionidmapper2-function.md) feita pelo tempo de execução atual.</span><span class="sxs-lookup"><span data-stu-id="357e1-108">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="357e1-109">O criador de perfil pode usar essas informações para fazer a ambiguidade entre tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="357e1-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="357e1-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="357e1-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="357e1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="357e1-111">Remarks</span></span>  
 <span data-ttu-id="357e1-112">As alternativas para os valores de FunctionID serão passadas para os ganchos de entrada/saída da função do criador de perfil ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)e [FunctionTailcall3](functiontailcall3-function.md); ou [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) que são especificados pelo método [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) ou [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .</span><span class="sxs-lookup"><span data-stu-id="357e1-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="357e1-113">O método `FunctionIDMapper2` pode ser definido apenas uma vez; é recomendável defini-lo no retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="357e1-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="357e1-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="357e1-114">Requirements</span></span>  
 <span data-ttu-id="357e1-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="357e1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="357e1-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="357e1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="357e1-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="357e1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="357e1-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="357e1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357e1-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="357e1-119">See also</span></span>

- [<span data-ttu-id="357e1-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="357e1-120">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="357e1-121">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="357e1-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="357e1-122">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="357e1-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="357e1-123">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="357e1-123">Profiling</span></span>](index.md)
