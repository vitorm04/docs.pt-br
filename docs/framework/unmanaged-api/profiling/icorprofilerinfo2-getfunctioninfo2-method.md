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
ms.openlocfilehash: 11f9a186f5ec5e3b9e718a3ccd43b35b66d28078
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433185"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="9e2e3-102">Método ICorProfilerInfo2::GetFunctionInfo2</span><span class="sxs-lookup"><span data-stu-id="9e2e3-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="9e2e3-103">Obtém a classe pai, o token de metadados e a `ClassID` de cada argumento de tipo, se presente, de uma função.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e2e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e2e3-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="9e2e3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e2e3-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="9e2e3-106">no A ID da função para a qual obter a classe pai e outras informações.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="9e2e3-107">no Um valor `COR_PRF_FRAME_INFO` que aponta para informações sobre um registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="9e2e3-108">fora Um ponteiro para a classe pai da função.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="9e2e3-109">fora Um ponteiro para o módulo no qual a classe pai da função é definida.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="9e2e3-110">fora Um ponteiro para o token de metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="9e2e3-111">no O tamanho da matriz de `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="9e2e3-112">fora Um ponteiro para o número total de `ClassID` valores.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="9e2e3-113">fora Uma matriz de valores `ClassID`, cada qual é a ID de um argumento de tipo da função.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="9e2e3-114">Quando o método retornar, `typeArgs` conterá alguns ou todos os valores de `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e2e3-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e2e3-115">Remarks</span></span>  
 <span data-ttu-id="9e2e3-116">O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de [metadados](../../../../docs/framework/unmanaged-api/metadata/index.md) para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="9e2e3-117">O token de metadados que é retornado para o local referenciado por `pToken` pode ser usado para acessar os metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="9e2e3-118">Os argumentos ID de classe e tipo retornados por meio dos parâmetros `pClassId` e `typeArgs` dependem do valor que é passado no parâmetro `frameInfo`, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="9e2e3-119">Valor do parâmetro `frameInfo`</span><span class="sxs-lookup"><span data-stu-id="9e2e3-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="9e2e3-120">Resultado</span><span class="sxs-lookup"><span data-stu-id="9e2e3-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="9e2e3-121">Um valor `COR_PRF_FRAME_INFO` que foi obtido de um retorno de chamada `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="9e2e3-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="9e2e3-122">O `ClassID`, retornado no local referenciado por `pClassId`e todos os argumentos de tipo, retornados na matriz de `typeArgs`, será exato.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="9e2e3-123">Um `COR_PRF_FRAME_INFO` que foi obtido de uma fonte diferente de um retorno de chamada `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="9e2e3-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="9e2e3-124">Os argumentos exatos `ClassID` e de tipo não podem ser determinados.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="9e2e3-125">Ou seja, o `ClassID` pode ser nulo e alguns argumentos de tipo podem voltar como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="9e2e3-126">Zero</span><span class="sxs-lookup"><span data-stu-id="9e2e3-126">Zero</span></span>|<span data-ttu-id="9e2e3-127">Os argumentos exatos `ClassID` e de tipo não podem ser determinados.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="9e2e3-128">Ou seja, o `ClassID` pode ser nulo e alguns argumentos de tipo podem voltar como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="9e2e3-129">Depois que `GetFunctionInfo2` retorna, você deve verificar se o buffer de `typeArgs` era grande o suficiente para conter todos os valores de `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="9e2e3-130">Para fazer isso, compare o valor que `pcTypeArgs` aponta com o valor do parâmetro `cTypeArgs`.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="9e2e3-131">Se `pcTypeArgs` apontar para um valor maior que `cTypeArgs` dividido pelo tamanho de um valor de `ClassID`, aloque um buffer de `pcTypeArgs` maior, atualize `cTypeArgs` com o tamanho novo, maior e chame `GetFunctionInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="9e2e3-132">Como alternativa, você pode primeiro chamar `GetFunctionInfo2` com um buffer de `pcTypeArgs` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9e2e3-133">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcTypeArgs` dividido pelo tamanho de um valor de `ClassID` e chamar `GetFunctionInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="9e2e3-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e2e3-134">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9e2e3-134">Requirements</span></span>  
 <span data-ttu-id="9e2e3-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e2e3-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e2e3-136">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9e2e3-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e2e3-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e2e3-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e2e3-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e2e3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2e3-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e2e3-139">See also</span></span>

- [<span data-ttu-id="9e2e3-140">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9e2e3-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="9e2e3-141">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="9e2e3-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="9e2e3-142">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9e2e3-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9e2e3-143">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9e2e3-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
