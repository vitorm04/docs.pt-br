---
title: Método ICorProfilerInfo2::GetFunctionInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7b6c19c87aceffd1e199975db6f16191bc3ddd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130267"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="b1531-102">Método ICorProfilerInfo2::GetFunctionInfo2</span><span class="sxs-lookup"><span data-stu-id="b1531-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="b1531-103">Obtém a classe pai, o token de metadados e o `ClassID` de cada argumento de tipo, se presente, de uma função.</span><span class="sxs-lookup"><span data-stu-id="b1531-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1531-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1531-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1531-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1531-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="b1531-106">[in] A ID da função para o qual obter o pai de classe e outras informações.</span><span class="sxs-lookup"><span data-stu-id="b1531-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="b1531-107">[in] Um `COR_PRF_FRAME_INFO` valor aponta para obter informações sobre um quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="b1531-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="b1531-108">[out] Um ponteiro para a classe pai da função.</span><span class="sxs-lookup"><span data-stu-id="b1531-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="b1531-109">[out] Um ponteiro para o módulo no qual a classe pai da função é definido.</span><span class="sxs-lookup"><span data-stu-id="b1531-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="b1531-110">[out] Um ponteiro para o token de metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="b1531-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="b1531-111">[in] O tamanho do `typeArgs` matriz.</span><span class="sxs-lookup"><span data-stu-id="b1531-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="b1531-112">[out] Um ponteiro para o número total de `ClassID` valores.</span><span class="sxs-lookup"><span data-stu-id="b1531-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="b1531-113">[out] Uma matriz de `ClassID` valores, cada uma delas é a ID de um argumento de tipo da função.</span><span class="sxs-lookup"><span data-stu-id="b1531-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="b1531-114">Quando o método retorna, `typeArgs` irá conter algumas ou todas as `ClassID` valores.</span><span class="sxs-lookup"><span data-stu-id="b1531-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1531-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1531-115">Remarks</span></span>  
 <span data-ttu-id="b1531-116">O código do criador de perfil pode chamar [ICorProfilerInfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma [metadados](../../../../docs/framework/unmanaged-api/metadata/index.md) interface para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="b1531-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="b1531-117">O token de metadados que é retornado para o local referenciado pelo `pToken` , em seguida, pode ser usado para acessar os metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="b1531-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="b1531-118">Os argumentos de ID e o tipo de classe que são retornados por meio de `pClassId` e `typeArgs` parâmetros dependem do valor que é passado a `frameInfo` parâmetro, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b1531-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="b1531-119">Valor da `frameInfo` parâmetro</span><span class="sxs-lookup"><span data-stu-id="b1531-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="b1531-120">Resultado</span><span class="sxs-lookup"><span data-stu-id="b1531-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="b1531-121">Um `COR_PRF_FRAME_INFO` valor que foi obtido um `FunctionEnter2` retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="b1531-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="b1531-122">O `ClassID`, retornada no local referenciado pela `pClassId`, e todos os tipo de argumentos, retornados no `typeArgs` de matriz, será exata.</span><span class="sxs-lookup"><span data-stu-id="b1531-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="b1531-123">Um `COR_PRF_FRAME_INFO` que foi obtido de uma fonte diferente de um `FunctionEnter2` retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="b1531-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="b1531-124">Exato `ClassID` e argumentos de tipo não podem ser determinados.</span><span class="sxs-lookup"><span data-stu-id="b1531-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="b1531-125">Ou seja, o `ClassID` podem ser nulos e alguns argumentos de tipo podem vir como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b1531-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="b1531-126">Zero</span><span class="sxs-lookup"><span data-stu-id="b1531-126">Zero</span></span>|<span data-ttu-id="b1531-127">Exato `ClassID` e argumentos de tipo não podem ser determinados.</span><span class="sxs-lookup"><span data-stu-id="b1531-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="b1531-128">Ou seja, o `ClassID` podem ser nulos e alguns argumentos de tipo podem vir como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b1531-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="b1531-129">Após `GetFunctionInfo2` é retornado, você deve verificar se o `typeArgs` buffer era grande o suficiente para conter todos os `ClassID` valores.</span><span class="sxs-lookup"><span data-stu-id="b1531-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="b1531-130">Para fazer isso, o valor de comparação que `pcTypeArgs` aponta para com o valor da `cTypeArgs` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b1531-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="b1531-131">Se `pcTypeArgs` aponta para um valor maior que `cTypeArgs` dividida pelo tamanho de uma `ClassID` o valor, alocar uma maior `pcTypeArgs` do buffer, atualize `cTypeArgs` com o novo e maior tamanho e a chamada `GetFunctionInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="b1531-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="b1531-132">Como alternativa, você pode primeiro chamar `GetFunctionInfo2` com um comprimento de zero `pcTypeArgs` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="b1531-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b1531-133">Em seguida, você pode definir o tamanho do buffer para o valor retornado na `pcTypeArgs` dividida pelo tamanho de um `ClassID` valor e chame `GetFunctionInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="b1531-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1531-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1531-134">Requirements</span></span>  
 <span data-ttu-id="b1531-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1531-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1531-136">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b1531-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1531-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1531-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1531-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1531-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1531-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1531-139">See also</span></span>

- [<span data-ttu-id="b1531-140">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b1531-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="b1531-141">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="b1531-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="b1531-142">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b1531-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b1531-143">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b1531-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
