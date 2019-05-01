---
title: Método ICorProfilerInfo3::GetFunctionEnter3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8df3700c6002e7a181d4882c4afd8542c6b6c93a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049525"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="80f49-102">Método ICorProfilerInfo3::GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="80f49-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="80f49-103">Fornece as informações de quadro e o argumento de pilha da função que está sendo relatada ao criador de perfil, o [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="80f49-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="80f49-104">Esse método pode ser chamado somente durante o `FunctionEnter3WithInfo` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="80f49-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80f49-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80f49-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80f49-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80f49-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="80f49-107">[in] O `FunctionID` da função que está sendo inserida.</span><span class="sxs-lookup"><span data-stu-id="80f49-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="80f49-108">[in] Um identificador opaco que representa informações sobre um registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="80f49-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="80f49-109">O criador de perfil deve fornecer os mesmos `eltInfo` que foi fornecido pelo [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="80f49-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="80f49-110">[out] Um identificador opaco que representa as informações sobre um registro de ativação genéricos.</span><span class="sxs-lookup"><span data-stu-id="80f49-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="80f49-111">Esse identificador é válido somente durante o `FunctionEnter3WithInfo` retorno de chamada em que o criador de perfil chamado o `GetFunctionEnter3Info` método.</span><span class="sxs-lookup"><span data-stu-id="80f49-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="80f49-112">[no, out] Um ponteiro para o tamanho total, em bytes, do [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) estrutura (além de outras [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estruturas para os intervalos de argumento apontados pelo `pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="80f49-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="80f49-113">Se o tamanho especificado não é suficiente, ERROR_INSUFFICIENT_BUFFER é retornado e o tamanho esperado é armazenado no `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="80f49-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="80f49-114">Para chamar `GetFunctionEnter3Info` apenas para recuperar o valor esperado `*pcbArgumentInfo`, defina `*pcbArgumentInfo`= 0 e `pArgumentInfo`= NULL.</span><span class="sxs-lookup"><span data-stu-id="80f49-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="80f49-115">[out] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) estrutura que descreve os locais dos argumentos da função na memória, em ordem da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="80f49-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80f49-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="80f49-116">Remarks</span></span>  
 <span data-ttu-id="80f49-117">O criador de perfil deve alocar espaço suficiente para o `COR_PRF_FUNCTION_ARGUMENT_INFO` estrutura da função que está sendo inspecionada e deve indicar o tamanho no `pcbArgumentInfo` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="80f49-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80f49-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80f49-118">Requirements</span></span>  
 <span data-ttu-id="80f49-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80f49-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80f49-120">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80f49-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80f49-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80f49-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80f49-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80f49-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f49-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80f49-123">See also</span></span>

- [<span data-ttu-id="80f49-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="80f49-124">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="80f49-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="80f49-125">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="80f49-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="80f49-126">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="80f49-127">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="80f49-127">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="80f49-128">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="80f49-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="80f49-129">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="80f49-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
