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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177014"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="a1a76-102">Método ICorProfilerInfo3::GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="a1a76-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="a1a76-103">Fornece o quadro de pilha e as informações de argumento da função que está sendo relatada ao profiler pela função [FunctionEnter3WithInfo.](functionenter3withinfo-function.md)</span><span class="sxs-lookup"><span data-stu-id="a1a76-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="a1a76-104">Este método só pode `FunctionEnter3WithInfo` ser chamado durante o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a1a76-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a76-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1a76-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1a76-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1a76-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a1a76-107">[em] A `FunctionID` função que está sendo inserida.</span><span class="sxs-lookup"><span data-stu-id="a1a76-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="a1a76-108">[em] Uma alça opaca que representa informações sobre um determinado quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="a1a76-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="a1a76-109">O profiler deve `eltInfo` fornecer o mesmo que foi dado pela função [FunctionEnter3WithInfo.](functionenter3withinfo-function.md)</span><span class="sxs-lookup"><span data-stu-id="a1a76-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="a1a76-110">[fora] Uma alça opaca que representa informações genéricas sobre um determinado quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="a1a76-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="a1a76-111">Esta alça é válida `FunctionEnter3WithInfo` somente durante o retorno `GetFunctionEnter3Info` de chamada no qual o profiler chamou o método.</span><span class="sxs-lookup"><span data-stu-id="a1a76-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="a1a76-112">[dentro, fora] Um ponteiro para o tamanho total, em bytes, da estrutura [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (mais quaisquer estruturas [adicionais de COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) para as faixas de argumento apontadas por `pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="a1a76-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="a1a76-113">Se o tamanho especificado não for suficiente, ERROR_INSUFFICIENT_BUFFER é `pcbArgumentInfo`devolvido e o tamanho esperado é armazenado em .</span><span class="sxs-lookup"><span data-stu-id="a1a76-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="a1a76-114">Para `GetFunctionEnter3Info` ligar apenas para recuperar `*pcbArgumentInfo`o `*pcbArgumentInfo`valor `pArgumentInfo`esperado para , definir =0 e =NULL.</span><span class="sxs-lookup"><span data-stu-id="a1a76-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="a1a76-115">[fora] Um ponteiro para uma estrutura [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) que descreve os locais dos argumentos da função na memória, na ordem da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="a1a76-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1a76-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1a76-116">Remarks</span></span>  
 <span data-ttu-id="a1a76-117">O profiler deve alocar `COR_PRF_FUNCTION_ARGUMENT_INFO` espaço suficiente para a estrutura da função que `pcbArgumentInfo` está sendo inspecionada, e deve indicar o tamanho no parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a1a76-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1a76-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1a76-118">Requirements</span></span>  
 <span data-ttu-id="a1a76-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1a76-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1a76-120">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1a76-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1a76-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1a76-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1a76-122">**.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1a76-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a76-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="a1a76-123">See also</span></span>

- [<span data-ttu-id="a1a76-124">Functionenter3withinfo</span><span class="sxs-lookup"><span data-stu-id="a1a76-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="a1a76-125">Functionleave3withinfo</span><span class="sxs-lookup"><span data-stu-id="a1a76-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a1a76-126">Functiontailcall3withinfo</span><span class="sxs-lookup"><span data-stu-id="a1a76-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a1a76-127">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="a1a76-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a1a76-128">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="a1a76-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a1a76-129">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a1a76-129">Profiling</span></span>](index.md)
