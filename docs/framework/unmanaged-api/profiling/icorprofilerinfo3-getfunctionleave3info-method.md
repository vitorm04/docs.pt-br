---
title: "Método ICorProfilerInfo3::GetFunctionLeave3Info"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5cbd73b6bfe89bec50eff0e09ec078db912adf25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="260a9-102">Método ICorProfilerInfo3::GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="260a9-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="260a9-103">Fornece o quadro de pilhas e o valor de retorno da função que está sendo relatado para o criador de perfil pelo [função FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="260a9-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="260a9-104">Esse método pode ser chamado somente durante o `FunctionLeave3WithInfo` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="260a9-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="260a9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="260a9-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="260a9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="260a9-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="260a9-107">[in] O `FunctionID` da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="260a9-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="260a9-108">[in] Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="260a9-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="260a9-109">O criador de perfil deve fornecer as mesmas `eltInfo` que foi fornecido para o criador de perfil, o [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="260a9-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="260a9-110">[out] Um identificador opaco que representa informações de genéricos sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="260a9-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="260a9-111">Esse identificador é válido somente durante o `FunctionLeave3WithInfo` que o criador de perfil de chamada de retorno de chamada a `GetFunctionLeave3Info` método.</span><span class="sxs-lookup"><span data-stu-id="260a9-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="260a9-112">[out] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estrutura que contém o valor retornado da função.</span><span class="sxs-lookup"><span data-stu-id="260a9-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="260a9-113">Para acessar informações do valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="260a9-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="260a9-114">O criador de perfil pode usar o [: SetEventMask método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="260a9-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="260a9-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="260a9-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="260a9-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="260a9-116">Requirements</span></span>  
 <span data-ttu-id="260a9-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="260a9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="260a9-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="260a9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="260a9-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="260a9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="260a9-120">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="260a9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="260a9-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="260a9-121">See Also</span></span>  
 [<span data-ttu-id="260a9-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="260a9-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="260a9-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="260a9-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="260a9-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="260a9-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="260a9-125">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="260a9-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="260a9-126">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="260a9-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="260a9-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="260a9-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
