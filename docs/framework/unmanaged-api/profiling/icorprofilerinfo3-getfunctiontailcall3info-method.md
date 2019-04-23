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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40e518e3cf5967d2b0a7eda8c7b58ec0f918e219
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187415"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="b763f-102">Método ICorProfilerInfo3::GetFunctionTailcall3Info</span><span class="sxs-lookup"><span data-stu-id="b763f-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="b763f-103">Fornece o quadro de pilhas da função que está sendo relatado ao criador de perfil, o [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="b763f-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="b763f-104">Esse método pode ser chamado somente durante o `FunctionTailcall3WithInfo` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b763f-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b763f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b763f-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b763f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b763f-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b763f-107">[in] O `FunctionID` da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="b763f-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b763f-108">[in] Um identificador opaco que representa informações sobre um registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="b763f-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b763f-109">O criador de perfil deve fornecer os mesmos `eltInfo` que foi fornecido para o criador de perfil pelo `FunctionTailcall3WithInfo` função.</span><span class="sxs-lookup"><span data-stu-id="b763f-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="b763f-110">[out] Um identificador opaco que representa as informações sobre um registro de ativação genéricos.</span><span class="sxs-lookup"><span data-stu-id="b763f-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="b763f-111">Esse identificador é válido somente durante o `FunctionTailcall3WithInfo` retorno de chamada em que o criador de perfil chamado o `GetFunctionTailcall3Info` método.</span><span class="sxs-lookup"><span data-stu-id="b763f-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b763f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="b763f-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b763f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b763f-113">Requirements</span></span>  
 <span data-ttu-id="b763f-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b763f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b763f-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b763f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b763f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b763f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b763f-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b763f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b763f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b763f-118">See also</span></span>

- [<span data-ttu-id="b763f-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b763f-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="b763f-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b763f-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="b763f-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b763f-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b763f-122">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="b763f-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b763f-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b763f-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b763f-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b763f-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
