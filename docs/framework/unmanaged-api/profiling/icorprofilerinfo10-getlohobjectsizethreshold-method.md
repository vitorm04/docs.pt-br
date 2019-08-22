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
ms.openlocfilehash: 8c9a85e9f00027f597795eea55a9bbb0364790f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661236"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>Método ICorProfilerInfo10:: GetLOHObjectSizeThreshold

Obtém o valor do limite de LOH (heap de objeto grande) configurado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a>Parâmetros

`pThreshold` \
fora O limite de heap de objeto grande em bytes.

## <a name="remarks"></a>Comentários

Os objetos maiores que o limite de heap de objeto grande serão alocados no heap de objeto grande. A partir do .NET Core 3,0, o limite de heap de objeto `pThreshold` grande é configurável, conterá o tamanho limite de heap de objeto grande ativo em bytes.

## <a name="requirements"></a>Requisitos

**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Cabeçalho:** CorProf.idl, CorProf.h

**Biblioteca** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
