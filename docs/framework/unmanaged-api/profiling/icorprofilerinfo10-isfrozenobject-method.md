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
ms.openlocfilehash: 05f25d8fb61a16f41a82a987529017db6a687740
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973986"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>Método ICorProfilerInfo10:: iscongeladoobject
  
 Dado um ObjectID, determina se o objeto está em um segmento somente leitura.   
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```  
  
#### <a name="parameters"></a>Parâmetros  
 
 `objectId` \
 no O objeto a ser examinado.

 `pbFrozen` \
 fora Um `BOOL` que indica se o objeto está em um segmento somente leitura.

## <a name="requirements"></a>Requisitos  
 **Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

