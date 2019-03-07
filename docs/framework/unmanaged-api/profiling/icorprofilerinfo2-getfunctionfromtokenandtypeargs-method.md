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
ms.openlocfilehash: c069cb375e9cb6011e7e91041d13736f5ef88dfd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482438"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="bf918-102">Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs</span><span class="sxs-lookup"><span data-stu-id="bf918-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="bf918-103">Obtém o `FunctionID` de uma função usando o token de metadados especificado, que contém a classe, e `ClassID` valores de qualquer tipo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="bf918-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf918-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf918-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf918-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf918-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="bf918-106">[in] A ID do módulo no qual a função reside.</span><span class="sxs-lookup"><span data-stu-id="bf918-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="bf918-107">[in] Um `mdMethodDef` token de metadados que faz referência à função.</span><span class="sxs-lookup"><span data-stu-id="bf918-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="bf918-108">[in] A ID de classe da função.</span><span class="sxs-lookup"><span data-stu-id="bf918-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="bf918-109">[in] O número de parâmetros de tipo para a função determinada.</span><span class="sxs-lookup"><span data-stu-id="bf918-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="bf918-110">Esse valor deve ser zero para funções não genéricos.</span><span class="sxs-lookup"><span data-stu-id="bf918-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="bf918-111">[in] Uma matriz de `ClassID` valores, cada um deles é um argumento da função.</span><span class="sxs-lookup"><span data-stu-id="bf918-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="bf918-112">O valor de `typeArgs` pode ser NULL se `cTypeArgs` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="bf918-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="bf918-113">[out] Um ponteiro para o `FunctionID` da função especificada.</span><span class="sxs-lookup"><span data-stu-id="bf918-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf918-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf918-114">Remarks</span></span>  
 <span data-ttu-id="bf918-115">Chamar o `GetFunctionFromTokenAndTypeArgs` método com um `mdMethodRef` metadados, em vez de um `mdMethodDef` token de metadados pode ter resultados imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="bf918-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="bf918-116">Os chamadores devem resolver o `mdMethodRef` para um `mdMethodDef` ao passá-la.</span><span class="sxs-lookup"><span data-stu-id="bf918-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="bf918-117">Se a função ainda não foi carregada, chamando `GetFunctionFromTokenAndTypeArgs` fará com que o carregamento ocorra, o que é uma operação perigosa em vários contextos.</span><span class="sxs-lookup"><span data-stu-id="bf918-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="bf918-118">Por exemplo, chamar esse método durante o carregamento de módulos ou tipos de poderia levar a um loop infinito como o tempo de execução tenta carregar circularmente as coisas.</span><span class="sxs-lookup"><span data-stu-id="bf918-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="bf918-119">Em geral, use de `GetFunctionFromTokenAndTypeArgs` não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="bf918-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="bf918-120">Se os criadores de perfis estiver interessados em eventos para uma função específica, eles devem armazenar o `ModuleID` e `mdMethodDef` dessa função, e use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) para verificar se um determinado `FunctionID` é o que a função desejada.</span><span class="sxs-lookup"><span data-stu-id="bf918-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf918-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf918-121">Requirements</span></span>  
 <span data-ttu-id="bf918-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf918-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf918-123">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf918-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf918-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf918-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf918-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf918-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf918-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf918-126">See also</span></span>
- [<span data-ttu-id="bf918-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="bf918-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="bf918-128">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="bf918-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
