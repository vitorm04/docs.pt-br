---
title: Método ICorProfilerInfo2::GetClassIDInfo2
ms.date: 03/30/2017
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
ms.openlocfilehash: 8ce02b8b44074bed2da9e302f95a67a528601bf8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433429"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="1c71a-102">Método ICorProfilerInfo2::GetClassIDInfo2</span><span class="sxs-lookup"><span data-stu-id="1c71a-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="1c71a-103">Obtém o módulo pai e o token de metadados para a definição genérica aberta da classe especificada, a `ClassID` de sua classe pai e a `ClassID` para cada argumento de tipo, se presente, da classe.</span><span class="sxs-lookup"><span data-stu-id="1c71a-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c71a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c71a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c71a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c71a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="1c71a-106">no A ID da classe para a qual as informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="1c71a-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="1c71a-107">fora Aponta para a ID do módulo pai para a definição genérica aberta da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="1c71a-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="1c71a-108">fora Ponteiro para o token de metadados para a definição genérica aberta da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="1c71a-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="1c71a-109">fora Ponteiro para a ID da classe pai.</span><span class="sxs-lookup"><span data-stu-id="1c71a-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="1c71a-110">no O tamanho da matriz de `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="1c71a-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="1c71a-111">fora Aponta para o número total de elementos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1c71a-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="1c71a-112">fora Uma matriz de valores de `ClassID`, cada um representando a ID de um argumento de tipo da classe.</span><span class="sxs-lookup"><span data-stu-id="1c71a-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="1c71a-113">Quando o método retornar, `typeArgs` conterá alguns ou todos os valores de `ClassID` disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1c71a-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c71a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c71a-114">Remarks</span></span>  
 <span data-ttu-id="1c71a-115">O método `GetClassIDInfo2` é semelhante ao método [ICorProfilerInfo:: GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) , mas `GetClassIDInfo2` Obtém informações adicionais sobre um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="1c71a-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="1c71a-116">O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de [metadados](../../../../docs/framework/unmanaged-api/metadata/index.md) para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="1c71a-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="1c71a-117">O token de metadados que é retornado para o local referenciado por `pTypeDefToken` pode ser usado para acessar os metadados da classe.</span><span class="sxs-lookup"><span data-stu-id="1c71a-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="1c71a-118">Depois que `GetClassIDInfo2` retorna, você deve verificar se o buffer de `typeArgs` era grande o suficiente para conter todos os valores de `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="1c71a-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="1c71a-119">Para fazer isso, compare o valor que `pcNumTypeArgs` aponta com o valor do parâmetro `cNumTypeArgs`.</span><span class="sxs-lookup"><span data-stu-id="1c71a-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="1c71a-120">Se `pcNumTypeArgs` apontar para um valor maior que `cNumTypeArgs`, aloque um buffer de `typeArgs` maior, atualize `cNumTypeArgs` com o tamanho novo, maior e chame `GetClassIDInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="1c71a-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="1c71a-121">Como alternativa, você pode primeiro chamar `GetClassIDInfo2` com um buffer de `typeArgs` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="1c71a-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1c71a-122">Em seguida, você pode definir o tamanho do buffer de `typeArgs` para o valor retornado em `pcNumTypeArgs` e chamar `GetClassIDInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="1c71a-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c71a-123">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1c71a-123">Requirements</span></span>  
 <span data-ttu-id="1c71a-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c71a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c71a-125">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1c71a-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c71a-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c71a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c71a-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c71a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c71a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c71a-128">See also</span></span>

- [<span data-ttu-id="1c71a-129">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="1c71a-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="1c71a-130">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="1c71a-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="1c71a-131">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1c71a-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1c71a-132">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1c71a-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
