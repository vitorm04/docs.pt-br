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
ms.openlocfilehash: 50b4de2de3e74a5835ee5706999892735269d4c2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861730"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="387fd-102">Método ICorProfilerInfo8:: IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="387fd-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="387fd-103">Determina se uma função não tem metadados associados.</span><span class="sxs-lookup"><span data-stu-id="387fd-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="387fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="387fd-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="387fd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="387fd-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="387fd-106">\[em] a `FunctionID` que identifica a função em questão.</span><span class="sxs-lookup"><span data-stu-id="387fd-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="387fd-107">\[out] um ponteiro para uma `BOOL` que conterá um valor que indica se a função não tem metadados.</span><span class="sxs-lookup"><span data-stu-id="387fd-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="387fd-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="387fd-108">Remarks</span></span>

<span data-ttu-id="387fd-109">Uma função será considerada dinâmica se não tiver metadados.</span><span class="sxs-lookup"><span data-stu-id="387fd-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="387fd-110">Determinados métodos, como stubs IL ou métodos LCG, não têm metadados associados que podem ser recuperados usando as APIs do IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="387fd-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="387fd-111">Esses métodos podem ser encontrados por infilers por meio de ponteiros de instrução ou ouvindo [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="387fd-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="387fd-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="387fd-112">Requirements</span></span>

<span data-ttu-id="387fd-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="387fd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="387fd-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="387fd-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="387fd-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="387fd-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="387fd-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="387fd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="387fd-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="387fd-117">See also</span></span>

- [<span data-ttu-id="387fd-118">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="387fd-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
