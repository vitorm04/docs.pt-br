---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: eaf33f3b0de7a18e400cd16d29c046784e2e190f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495314"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="3196f-102">Método ICorProfilerInfo8:: GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="3196f-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="3196f-103">Recupera informações sobre métodos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="3196f-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="3196f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3196f-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="3196f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3196f-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="3196f-106">\[in] a ID da função para a qual recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="3196f-106">\[in] The ID of the function for which to retrieve information.</span></span>

- `moduleId`

  <span data-ttu-id="3196f-107">\[in] um ponteiro para o módulo no qual a classe pai da função é definida.</span><span class="sxs-lookup"><span data-stu-id="3196f-107">\[in] A pointer to the module in which the function's parent class is defined.</span></span>

- `ppvSig`

  <span data-ttu-id="3196f-108">\[out] um ponteiro para a assinatura da função.</span><span class="sxs-lookup"><span data-stu-id="3196f-108">\[out] A pointer to the signature for the function.</span></span>

- `pbSig`

  <span data-ttu-id="3196f-109">\[out] um ponteiro para a contagem de bytes para a assinatura de função.</span><span class="sxs-lookup"><span data-stu-id="3196f-109">\[out] A pointer to the count of bytes for the function signature.</span></span>

- `cchName`

  <span data-ttu-id="3196f-110">\[in] o tamanho máximo da `wszName` matriz.</span><span class="sxs-lookup"><span data-stu-id="3196f-110">\[in] The maximum size of the `wszName` array.</span></span>

- `pcchName`

  <span data-ttu-id="3196f-111">\[out] o número de caracteres na `wszName` matriz.</span><span class="sxs-lookup"><span data-stu-id="3196f-111">\[out] The number of characters in the `wszName` array.</span></span>

- `wszName`

  <span data-ttu-id="3196f-112">\[out] uma matriz de `WCHAR` que é o nome da função, se houver uma.</span><span class="sxs-lookup"><span data-stu-id="3196f-112">\[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="3196f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3196f-113">Remarks</span></span>

<span data-ttu-id="3196f-114">Determinados métodos, como stubs IL ou LCG, não têm metadados associados que podem ser recuperados usando as APIs [IMetaDataImport](../metadata/imetadataimport-interface.md) e [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3196f-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="3196f-115">Esses métodos podem ser encontrados por infilers por meio de ponteiros de instrução ou ouvindo [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="3196f-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="3196f-116">Essa API pode ser usada para recuperar informações sobre métodos dinâmicos, incluindo um nome amigável, se disponível.</span><span class="sxs-lookup"><span data-stu-id="3196f-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="3196f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3196f-117">Requirements</span></span>

<span data-ttu-id="3196f-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3196f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3196f-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3196f-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="3196f-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3196f-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3196f-121">**.NET Framework versões:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3196f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3196f-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="3196f-122">See also</span></span>

- [<span data-ttu-id="3196f-123">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="3196f-123">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
