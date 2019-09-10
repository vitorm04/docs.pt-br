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
ms.openlocfilehash: 01aa1df27dccf41060083333588e04bc5ea88520
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855931"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>Método ICorProfilerInfo8:: IsFunctionDynamic

Determina se uma função não tem metadados associados.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

#### <a name="parameters"></a>Parâmetros

`functionId` \
no  O `FunctionID` que identifica a função em questão.

`isDynamic` \
fora Um ponteiro para um `BOOL` que conterá um valor que indica se a função não tem metadados.

## <a name="remarks"></a>Comentários

Uma função será considerada dinâmica se não tiver metadados. Determinados métodos, como stubs IL ou métodos LCG, não têm metadados associados que podem ser recuperados usando as APIs do IMetaDataImport. Esses métodos podem ser encontrados por infilers por meio de ponteiros de instrução ou ouvindo [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

## <a name="requirements"></a>Requisitos

**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorProf.idl, CorProf.h

**Biblioteca** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
