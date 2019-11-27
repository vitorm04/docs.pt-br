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
ms.openlocfilehash: 41021a524142afe34727584265aee578e31a64b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433214"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="7aafd-102">Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs</span><span class="sxs-lookup"><span data-stu-id="7aafd-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="7aafd-103">Obtém a `FunctionID` de uma função usando o token de metadados especificado, contendo a classe e valores de `ClassID` de qualquer argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="7aafd-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aafd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7aafd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aafd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7aafd-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="7aafd-106">no A ID do módulo no qual a função reside.</span><span class="sxs-lookup"><span data-stu-id="7aafd-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="7aafd-107">no Um `mdMethodDef` token de metadados que faz referência à função.</span><span class="sxs-lookup"><span data-stu-id="7aafd-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="7aafd-108">no A ID da classe que contém a função.</span><span class="sxs-lookup"><span data-stu-id="7aafd-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="7aafd-109">no O número de parâmetros de tipo para a função fornecida.</span><span class="sxs-lookup"><span data-stu-id="7aafd-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="7aafd-110">Esse valor deve ser zero para funções não genéricas.</span><span class="sxs-lookup"><span data-stu-id="7aafd-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="7aafd-111">no Uma matriz de valores de `ClassID`, cada um dos quais é um argumento da função.</span><span class="sxs-lookup"><span data-stu-id="7aafd-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="7aafd-112">O valor de `typeArgs` pode ser nulo se `cTypeArgs` for definido como zero.</span><span class="sxs-lookup"><span data-stu-id="7aafd-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="7aafd-113">fora Um ponteiro para a `FunctionID` da função especificada.</span><span class="sxs-lookup"><span data-stu-id="7aafd-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7aafd-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="7aafd-114">Remarks</span></span>  
 <span data-ttu-id="7aafd-115">Chamar o método `GetFunctionFromTokenAndTypeArgs` com um `mdMethodRef` metadados em vez de um token de metadados `mdMethodDef` pode ter resultados imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="7aafd-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="7aafd-116">Os chamadores devem resolver o `mdMethodRef` a um `mdMethodDef` ao passá-lo.</span><span class="sxs-lookup"><span data-stu-id="7aafd-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="7aafd-117">Se a função ainda não estiver carregada, chamar `GetFunctionFromTokenAndTypeArgs` fará com que o carregamento ocorra, que é uma operação perigosa em muitos contextos.</span><span class="sxs-lookup"><span data-stu-id="7aafd-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="7aafd-118">Por exemplo, chamar esse método durante o carregamento de módulos ou tipos pode levar a um loop infinito, pois o tempo de execução tenta carregar as coisas de forma circular.</span><span class="sxs-lookup"><span data-stu-id="7aafd-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="7aafd-119">Em geral, o uso de `GetFunctionFromTokenAndTypeArgs` não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="7aafd-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="7aafd-120">Se os profileres estiverem interessados em eventos para uma função específica, eles deverão armazenar o `ModuleID` e `mdMethodDef` dessa função e usar [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) para verificar se um determinado `FunctionID` é o da função desejada.</span><span class="sxs-lookup"><span data-stu-id="7aafd-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aafd-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7aafd-121">Requirements</span></span>  
 <span data-ttu-id="7aafd-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aafd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aafd-123">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7aafd-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7aafd-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7aafd-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aafd-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aafd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aafd-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7aafd-126">See also</span></span>

- [<span data-ttu-id="7aafd-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7aafd-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7aafd-128">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="7aafd-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
