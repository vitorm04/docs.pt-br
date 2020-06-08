---
title: Método ICorProfilerInfo3::GetFunctionLeave3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: bab52d9179d7454cab4a47e1a2bfe80a49b00c2a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502828"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="73d1a-102">Método ICorProfilerInfo3::GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="73d1a-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="73d1a-103">Fornece o quadro de pilha e o valor de retorno da função que está sendo relatada ao criador de perfil pela função de [função FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="73d1a-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="73d1a-104">Esse método pode ser chamado somente durante o `FunctionLeave3WithInfo` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="73d1a-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d1a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73d1a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73d1a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73d1a-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="73d1a-107">no O `FunctionID` da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="73d1a-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="73d1a-108">no Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="73d1a-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="73d1a-109">O criador de perfil deve fornecer o mesmo `eltInfo` que foi dado ao criador de perfil pela função [FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="73d1a-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="73d1a-110">fora Um identificador opaco que representa informações genéricas sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="73d1a-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="73d1a-111">Esse identificador é válido somente durante o `FunctionLeave3WithInfo` retorno de chamada no qual o criador de perfil chamou o `GetFunctionLeave3Info` método.</span><span class="sxs-lookup"><span data-stu-id="73d1a-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="73d1a-112">fora Um ponteiro para uma estrutura de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) que contém o valor retornado da função.</span><span class="sxs-lookup"><span data-stu-id="73d1a-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="73d1a-113">Para acessar informações de valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="73d1a-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="73d1a-114">O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="73d1a-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73d1a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="73d1a-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73d1a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73d1a-116">Requirements</span></span>  
 <span data-ttu-id="73d1a-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73d1a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73d1a-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="73d1a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73d1a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73d1a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73d1a-120">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73d1a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d1a-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="73d1a-121">See also</span></span>

- [<span data-ttu-id="73d1a-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="73d1a-122">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="73d1a-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="73d1a-123">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="73d1a-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="73d1a-124">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="73d1a-125">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="73d1a-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="73d1a-126">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="73d1a-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="73d1a-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="73d1a-127">Profiling</span></span>](index.md)
