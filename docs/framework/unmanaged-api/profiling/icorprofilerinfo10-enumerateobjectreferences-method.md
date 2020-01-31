---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7fd62e0d3d9173f3b75882131e57126075c0677f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863303"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>Método ICorProfilerInfo10:: EnumerateObjectReferences

Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a>Parâmetros

- `objectId`

  \[em] o objeto no qual enumerar referências.

- `callback`

  \[em] a função que será chamada com as referências para o objeto.

- `clientData`

  \[em] dados fornecidos pelo Profiler para passar para a função `callback`.

## <a name="remarks"></a>Comentários

O método `EnumerateObjectReferences` é semelhante a [ObjectReferences](icorprofilercallback-objectreferences-method.md), exceto pelo fato de que ele percorre as referências sob demanda para o criador de perfil em vez de alocar previamente uma matriz para armazenar as referências.

## <a name="requirements"></a>Requisitos do

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
