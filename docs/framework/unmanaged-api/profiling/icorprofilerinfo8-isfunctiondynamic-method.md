---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c88279d361ea78a2e910c4621e92c500902d9124
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495119"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="0d8c9-102">Método ICorProfilerInfo8:: IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="0d8c9-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="0d8c9-103">Determina se uma função não tem metadados associados.</span><span class="sxs-lookup"><span data-stu-id="0d8c9-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d8c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d8c9-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="0d8c9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d8c9-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="0d8c9-106">\[in], o `FunctionID` que identifica a função em questão.</span><span class="sxs-lookup"><span data-stu-id="0d8c9-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="0d8c9-107">\[out] um ponteiro para um `BOOL` que conterá um valor que indica se a função não tem metadados.</span><span class="sxs-lookup"><span data-stu-id="0d8c9-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d8c9-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d8c9-108">Remarks</span></span>

<span data-ttu-id="0d8c9-109">Uma função será considerada dinâmica se não tiver metadados.</span><span class="sxs-lookup"><span data-stu-id="0d8c9-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="0d8c9-110">Determinados métodos, como stubs IL ou métodos LCG, não têm metadados associados que podem ser recuperados usando as APIs do IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="0d8c9-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="0d8c9-111">Esses métodos podem ser encontrados por infilers por meio de ponteiros de instrução ou ouvindo [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="0d8c9-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0d8c9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d8c9-112">Requirements</span></span>

<span data-ttu-id="0d8c9-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d8c9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0d8c9-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0d8c9-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0d8c9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d8c9-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0d8c9-116">**.NET Framework versões:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0d8c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0d8c9-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d8c9-117">See also</span></span>

- [<span data-ttu-id="0d8c9-118">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="0d8c9-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
