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
ms.openlocfilehash: 55411f187e2ef73997633d94b37a7d5d2cfd74c9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868558"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="578b7-102">Método ICorProfilerInfo3::GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="578b7-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="578b7-103">Fornece o quadro de pilha e as informações de argumento da função que está sendo relatada para o criador de perfil pela função [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="578b7-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="578b7-104">Esse método pode ser chamado somente durante o retorno de chamada `FunctionEnter3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="578b7-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="578b7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="578b7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="578b7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="578b7-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="578b7-107">no O `FunctionID` da função que está sendo inserida.</span><span class="sxs-lookup"><span data-stu-id="578b7-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="578b7-108">no Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="578b7-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="578b7-109">O criador de perfil deve fornecer o mesmo `eltInfo` que foi fornecido pela função [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="578b7-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="578b7-110">fora Um identificador opaco que representa informações genéricas sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="578b7-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="578b7-111">Esse identificador é válido somente durante o retorno de chamada `FunctionEnter3WithInfo` no qual o criador de perfil chamou o método `GetFunctionEnter3Info`.</span><span class="sxs-lookup"><span data-stu-id="578b7-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="578b7-112">[entrada, saída] Um ponteiro para o tamanho total, em bytes, da estrutura de [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (mais quaisquer estruturas de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) adicionais para os intervalos de argumentos apontados por `pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="578b7-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="578b7-113">Se o tamanho especificado não for suficiente, ERROR_INSUFFICIENT_BUFFER será retornado e o tamanho esperado será armazenado em `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="578b7-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="578b7-114">Para chamar `GetFunctionEnter3Info` apenas para recuperar o valor esperado para `*pcbArgumentInfo`, defina `*pcbArgumentInfo`= 0 e `pArgumentInfo`= NULL.</span><span class="sxs-lookup"><span data-stu-id="578b7-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="578b7-115">fora Um ponteiro para uma estrutura de [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) que descreve os locais dos argumentos da função na memória, na ordem da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="578b7-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="578b7-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="578b7-116">Remarks</span></span>  
 <span data-ttu-id="578b7-117">O criador de perfil deve alocar espaço suficiente para a estrutura de `COR_PRF_FUNCTION_ARGUMENT_INFO` da função que está sendo inspecionada e deve indicar o tamanho no parâmetro `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="578b7-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="578b7-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="578b7-118">Requirements</span></span>  
 <span data-ttu-id="578b7-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="578b7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="578b7-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="578b7-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="578b7-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="578b7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="578b7-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="578b7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="578b7-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="578b7-123">See also</span></span>

- [<span data-ttu-id="578b7-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="578b7-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="578b7-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="578b7-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="578b7-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="578b7-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="578b7-127">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="578b7-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="578b7-128">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="578b7-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="578b7-129">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="578b7-129">Profiling</span></span>](index.md)
