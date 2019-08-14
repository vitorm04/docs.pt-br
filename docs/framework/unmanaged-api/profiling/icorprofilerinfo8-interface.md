---
title: Interface ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973816"
---
# <a name="icorprofilerinfo8-interface"></a>Interface ICorProfilerInfo8

Uma subclasse de [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) que fornece métodos para consultar informações sobre métodos dinâmicos.

## <a name="methods"></a>Métodos  

| Método|Descrição|  
| ------------|-----------------|  
|[Método IsFunctionDynamic](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| Determina se uma função não tem metadados associados.|
|[Método GetFunctionFromIP3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| Mapeia um ponteiro de instrução de código gerenciado para uma FunctionID. Esse método funciona para métodos dinâmicos e não dinâmicos. |
|[Método GetDynamicFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Recupera informações sobre métodos dinâmicos. |

## <a name="requirements"></a>Requisitos  
**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** CorProf.idl, CorProf.h  
**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
## <a name="see-also"></a>Consulte também
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
