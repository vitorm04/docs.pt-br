---
title: Método ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ece4041f7fe4f9080db32a7edc2271b7f3beb95
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498933"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="3bef3-102">Método ICorProfilerInfo2::GetClassFromTokenAndTypeArgs</span><span class="sxs-lookup"><span data-stu-id="3bef3-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="3bef3-103">Obtém o `ClassID` de um tipo usando o token de metadados especificado e o `ClassID` valores de qualquer tipo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="3bef3-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bef3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bef3-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bef3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3bef3-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="3bef3-106">[in] A ID do módulo no qual reside o tipo.</span><span class="sxs-lookup"><span data-stu-id="3bef3-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="3bef3-107">[in] Um `mdTypeDef` token de metadados que faz referência ao tipo.</span><span class="sxs-lookup"><span data-stu-id="3bef3-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="3bef3-108">[in] O número de parâmetros de tipo para o tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="3bef3-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="3bef3-109">Esse valor deve ser zero para tipos não genéricos.</span><span class="sxs-lookup"><span data-stu-id="3bef3-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="3bef3-110">[in] Uma matriz de `ClassID` valores, cada um deles é um argumento do tipo.</span><span class="sxs-lookup"><span data-stu-id="3bef3-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="3bef3-111">O valor de `typeArgs` pode ser NULL se `cTypeArgs` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="3bef3-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="3bef3-112">[out] Um ponteiro para o `ClassID` do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="3bef3-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bef3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3bef3-113">Remarks</span></span>  
 <span data-ttu-id="3bef3-114">Chamar o `GetClassFromTokenAndTypeArgs` método com um `mdTypeRef` em vez de uma `mdTypeDef` token de metadados pode ter resultados imprevisíveis; os chamadores devem resolver o `mdTypeRef` para um `mdTypeDef` ao passá-la.</span><span class="sxs-lookup"><span data-stu-id="3bef3-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="3bef3-115">Se o tipo já não estiver carregado, chamando `GetClassFromTokenAndTypeArgs` irá disparar o carregamento, o que é uma operação perigosa em vários contextos.</span><span class="sxs-lookup"><span data-stu-id="3bef3-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="3bef3-116">Por exemplo, chamar esse método durante o carregamento dos módulos ou outros tipos poderia levar a um loop infinito como o tempo de execução tenta carregar circularmente as coisas.</span><span class="sxs-lookup"><span data-stu-id="3bef3-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="3bef3-117">Em geral, use de `GetClassFromTokenAndTypeArgs` não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="3bef3-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="3bef3-118">Se os criadores de perfis estiver interessados em eventos para um determinado tipo, deve armazenar o `ModuleID` e `mdTypeDef` do tipo e use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) para verificar se um determinado `ClassID` é o da tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="3bef3-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bef3-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3bef3-119">Requirements</span></span>  
 <span data-ttu-id="3bef3-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bef3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bef3-121">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3bef3-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3bef3-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bef3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bef3-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bef3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bef3-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bef3-124">See also</span></span>
- [<span data-ttu-id="3bef3-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="3bef3-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="3bef3-126">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="3bef3-126">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
