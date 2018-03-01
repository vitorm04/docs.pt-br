---
title: "Método ICorProfilerInfo2::GetClassIDInfo2"
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
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0348462cdbff14486b31e1878f06b7565b47182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="7e03c-102">Método ICorProfilerInfo2::GetClassIDInfo2</span><span class="sxs-lookup"><span data-stu-id="7e03c-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="7e03c-103">Obtém o módulo de pai e os metadados de token para a definição genérica aberta da classe especificada, o `ClassID` de sua classe pai e o `ClassID` para cada argumento de tipo, se houver, da classe.</span><span class="sxs-lookup"><span data-stu-id="7e03c-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e03c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e03c-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e03c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e03c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="7e03c-106">[in] A ID da classe para a qual as informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="7e03c-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="7e03c-107">[out] Ponteiro para a ID do módulo principal para a definição genérica aberta da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="7e03c-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="7e03c-108">[out] Ponteiro para o token de metadados para a definição genérica aberta da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="7e03c-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="7e03c-109">[out] Ponteiro para a ID da classe pai.</span><span class="sxs-lookup"><span data-stu-id="7e03c-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="7e03c-110">[in] O tamanho do `typeArgs` matriz.</span><span class="sxs-lookup"><span data-stu-id="7e03c-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="7e03c-111">[out] Ponteiro para o número total de elementos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7e03c-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="7e03c-112">[out] Uma matriz de `ClassID` valores, cada um deles representa a ID de um argumento de tipo da classe.</span><span class="sxs-lookup"><span data-stu-id="7e03c-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="7e03c-113">Quando o método retorna, `typeArgs` conterá alguns ou todos os disponíveis `ClassID` valores.</span><span class="sxs-lookup"><span data-stu-id="7e03c-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e03c-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e03c-114">Remarks</span></span>  
 <span data-ttu-id="7e03c-115">O `GetClassIDInfo2` método é semelhante do [: Getclassidinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) método, mas `GetClassIDInfo2` obtém informações adicionais sobre um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="7e03c-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="7e03c-116">O criador de perfil código pode chamar [Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter um [metadados](../../../../docs/framework/unmanaged-api/metadata/index.md) interface para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="7e03c-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="7e03c-117">O token de metadados que é retornado para o local referenciado pelo `pTypeDefToken` , em seguida, pode ser usado para acessar os metadados para a classe.</span><span class="sxs-lookup"><span data-stu-id="7e03c-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="7e03c-118">Depois de `GetClassIDInfo2` retorna, você deve verificar se o `typeArgs` buffer era grande o suficiente para conter todos o `ClassID` valores.</span><span class="sxs-lookup"><span data-stu-id="7e03c-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="7e03c-119">Para fazer isso, o valor de comparação que `pcNumTypeArgs` aponta para com o valor de `cNumTypeArgs` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7e03c-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="7e03c-120">Se `pcNumTypeArgs` aponta para um valor que é maior do que `cNumTypeArgs`, alocar uma maior `typeArgs` buffer, atualize `cNumTypeArgs` com o novo tamanho maior e chame `GetClassIDInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="7e03c-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="7e03c-121">Como alternativa, você pode primeiro chamar `GetClassIDInfo2` com um comprimento zero `typeArgs` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="7e03c-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7e03c-122">Você pode definir o `typeArgs` de buffer de tamanho para o valor retornado em `pcNumTypeArgs` e chame `GetClassIDInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="7e03c-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e03c-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e03c-123">Requirements</span></span>  
 <span data-ttu-id="7e03c-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e03c-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e03c-125">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e03c-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e03c-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e03c-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e03c-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e03c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e03c-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e03c-128">See Also</span></span>  
 [<span data-ttu-id="7e03c-129">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7e03c-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="7e03c-130">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="7e03c-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="7e03c-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7e03c-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="7e03c-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7e03c-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
