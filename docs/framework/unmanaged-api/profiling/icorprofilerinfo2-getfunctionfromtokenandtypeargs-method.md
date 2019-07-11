---
title: Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31fad9e82d0b93360f92676f6357c136ae60634a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771121"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="41190-102">Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs</span><span class="sxs-lookup"><span data-stu-id="41190-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="41190-103">Obtém o `FunctionID` de uma função usando o token de metadados especificado, que contém a classe, e `ClassID` valores de qualquer tipo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="41190-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41190-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41190-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41190-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41190-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="41190-106">[in] A ID do módulo no qual a função reside.</span><span class="sxs-lookup"><span data-stu-id="41190-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="41190-107">[in] Um `mdMethodDef` token de metadados que faz referência à função.</span><span class="sxs-lookup"><span data-stu-id="41190-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="41190-108">[in] A ID de classe da função.</span><span class="sxs-lookup"><span data-stu-id="41190-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="41190-109">[in] O número de parâmetros de tipo para a função determinada.</span><span class="sxs-lookup"><span data-stu-id="41190-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="41190-110">Esse valor deve ser zero para funções não genéricos.</span><span class="sxs-lookup"><span data-stu-id="41190-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="41190-111">[in] Uma matriz de `ClassID` valores, cada um deles é um argumento da função.</span><span class="sxs-lookup"><span data-stu-id="41190-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="41190-112">O valor de `typeArgs` pode ser NULL se `cTypeArgs` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="41190-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="41190-113">[out] Um ponteiro para o `FunctionID` da função especificada.</span><span class="sxs-lookup"><span data-stu-id="41190-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41190-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="41190-114">Remarks</span></span>  
 <span data-ttu-id="41190-115">Chamar o `GetFunctionFromTokenAndTypeArgs` método com um `mdMethodRef` metadados, em vez de um `mdMethodDef` token de metadados pode ter resultados imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="41190-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="41190-116">Os chamadores devem resolver o `mdMethodRef` para um `mdMethodDef` ao passá-la.</span><span class="sxs-lookup"><span data-stu-id="41190-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="41190-117">Se a função ainda não foi carregada, chamando `GetFunctionFromTokenAndTypeArgs` fará com que o carregamento ocorra, o que é uma operação perigosa em vários contextos.</span><span class="sxs-lookup"><span data-stu-id="41190-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="41190-118">Por exemplo, chamar esse método durante o carregamento de módulos ou tipos de poderia levar a um loop infinito como o tempo de execução tenta carregar circularmente as coisas.</span><span class="sxs-lookup"><span data-stu-id="41190-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="41190-119">Em geral, use de `GetFunctionFromTokenAndTypeArgs` não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="41190-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="41190-120">Se os criadores de perfis estiver interessados em eventos para uma função específica, eles devem armazenar o `ModuleID` e `mdMethodDef` dessa função, e use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) para verificar se um determinado `FunctionID` é o que a função desejada.</span><span class="sxs-lookup"><span data-stu-id="41190-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41190-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41190-121">Requirements</span></span>  
 <span data-ttu-id="41190-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41190-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41190-123">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41190-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41190-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41190-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41190-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41190-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41190-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41190-126">See also</span></span>

- [<span data-ttu-id="41190-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="41190-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="41190-128">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="41190-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
