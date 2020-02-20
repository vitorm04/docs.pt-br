---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7a0f6f6bea5bc919ebfe9c9acc3b02a31eaa7cd0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452208"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>Método ICorProfilerInfo10:: GetLOHObjectSizeThreshold

Obtém o valor do limite de LOH (heap de objeto grande) configurado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>parâmetros

- `pThreshold`

  \[out] o limite de heap de objeto grande em bytes.

## <a name="remarks"></a>Comentários

Os objetos maiores que o limite de heap de objeto grande serão alocados no heap de objeto grande. A partir do .NET Core 3,0, o limite de heap de objeto grande é configurável, `pThreshold` conterá o tamanho limite de heap de objeto grande ativo em bytes.

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Confira também

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
