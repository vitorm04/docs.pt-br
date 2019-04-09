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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d51462017287d42fd468ed0a74a2e83203a3d94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172387"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="83f40-102">Método ICorProfilerInfo3::GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="83f40-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="83f40-103">Fornece o quadro de pilha e o valor de retorno da função que está sendo relatada ao criador de perfil pela [função FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="83f40-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="83f40-104">Esse método pode ser chamado somente durante o `FunctionLeave3WithInfo` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="83f40-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f40-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83f40-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83f40-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83f40-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="83f40-107">[in] O `FunctionID` da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="83f40-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="83f40-108">[in] Um identificador opaco que representa informações sobre um registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="83f40-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="83f40-109">O criador de perfil deve fornecer os mesmos `eltInfo` que foi fornecido para o criador de perfil, o [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="83f40-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="83f40-110">[out] Um identificador opaco que representa as informações sobre um registro de ativação genéricos.</span><span class="sxs-lookup"><span data-stu-id="83f40-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="83f40-111">Esse identificador é válido somente durante o `FunctionLeave3WithInfo` retorno de chamada em que o criador de perfil chamado o `GetFunctionLeave3Info` método.</span><span class="sxs-lookup"><span data-stu-id="83f40-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="83f40-112">[out] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estrutura que contém o valor retornado da função.</span><span class="sxs-lookup"><span data-stu-id="83f40-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="83f40-113">Para acessar informações de valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="83f40-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="83f40-114">O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="83f40-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83f40-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="83f40-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83f40-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83f40-116">Requirements</span></span>  
 <span data-ttu-id="83f40-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83f40-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f40-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83f40-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83f40-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83f40-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="83f40-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="83f40-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83f40-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83f40-121">See also</span></span>

- [<span data-ttu-id="83f40-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="83f40-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="83f40-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="83f40-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="83f40-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="83f40-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="83f40-125">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="83f40-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="83f40-126">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="83f40-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="83f40-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="83f40-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
