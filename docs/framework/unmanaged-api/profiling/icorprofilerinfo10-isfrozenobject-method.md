---
title: 'ICorProfilerInfo10:: iscongeladoobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 21f9cb415f913a9c865a487f6e80523344db811e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452182"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>Método ICorProfilerInfo10:: iscongeladoobject

Dado um ObjectID, determina se o objeto está em um segmento somente leitura.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a>parâmetros

- `objectId`

  \[em] o objeto a ser examinado.

- `pbFrozen`

  \[out] uma `BOOL` indicando se o objeto está em um segmento somente leitura.

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Confira também

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
