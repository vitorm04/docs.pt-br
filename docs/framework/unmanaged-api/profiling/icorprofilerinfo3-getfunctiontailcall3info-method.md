---
title: Método ICorProfilerInfo3::GetFunctionTailcall3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176988"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="a03e9-102">Método ICorProfilerInfo3::GetFunctionTailcall3Info</span><span class="sxs-lookup"><span data-stu-id="a03e9-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="a03e9-103">Fornece o quadro de pilha da função que está sendo relatada ao profiler pela função [FunctionTailcall3WithInfo.](functiontailcall3withinfo-function.md)</span><span class="sxs-lookup"><span data-stu-id="a03e9-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="a03e9-104">Este método só pode `FunctionTailcall3WithInfo` ser chamado durante o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a03e9-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a03e9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a03e9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a03e9-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a03e9-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a03e9-107">[em] A `FunctionID` função que está voltando.</span><span class="sxs-lookup"><span data-stu-id="a03e9-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="a03e9-108">[em] Uma alça opaca que representa informações sobre um determinado quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="a03e9-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="a03e9-109">O profiler deve `eltInfo` fornecer o mesmo que foi `FunctionTailcall3WithInfo` dado ao profiler pela função.</span><span class="sxs-lookup"><span data-stu-id="a03e9-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="a03e9-110">[fora] Uma alça opaca que representa informações genéricas sobre um determinado quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="a03e9-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="a03e9-111">Esta alça é válida `FunctionTailcall3WithInfo` somente durante o retorno `GetFunctionTailcall3Info` de chamada no qual o profiler chamou o método.</span><span class="sxs-lookup"><span data-stu-id="a03e9-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a03e9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a03e9-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a03e9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a03e9-113">Requirements</span></span>  
 <span data-ttu-id="a03e9-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a03e9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a03e9-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a03e9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a03e9-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a03e9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a03e9-117">**.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a03e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03e9-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="a03e9-118">See also</span></span>

- [<span data-ttu-id="a03e9-119">Functionenter3withinfo</span><span class="sxs-lookup"><span data-stu-id="a03e9-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="a03e9-120">Functionleave3withinfo</span><span class="sxs-lookup"><span data-stu-id="a03e9-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a03e9-121">Functiontailcall3withinfo</span><span class="sxs-lookup"><span data-stu-id="a03e9-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a03e9-122">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="a03e9-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a03e9-123">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="a03e9-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a03e9-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a03e9-124">Profiling</span></span>](index.md)
