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
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974016"
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

