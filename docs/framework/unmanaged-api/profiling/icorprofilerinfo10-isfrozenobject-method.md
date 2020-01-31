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
ms.openlocfilehash: b6dabefceba038a129148f7ba36d4ffcfc425c80
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790034"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>Método ICorProfilerInfo10:: iscongeladoobject

Dado um ObjectID, determina se o objeto está em um segmento somente leitura.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a>Parâmetros

- `objectId`

  \[em] o objeto a ser examinado.

- `pbFrozen`

  \[out] uma `BOOL` indicando se o objeto está em um segmento somente leitura.

## <a name="requirements"></a>Requisitos do

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
