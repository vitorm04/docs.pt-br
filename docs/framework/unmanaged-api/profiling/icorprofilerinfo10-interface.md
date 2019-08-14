---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 496959ecac5b16f1faa138aec90c5194d15cb105
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974006"
---
# <a name="icorprofilerinfo10-interface"></a>Interface ICorProfilerInfo10

Uma subclasse de [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) que fornece métodos para modificar o Il da função, consultar informações do tempo de execução e suspender e retomar o tempo de execução.

## <a name="methods"></a>Métodos  

| Método|Descrição|  
| ------------|-----------------|  
|[Método EnumerateObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver). |
|[Método iscongeladoobject](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|Dado um ObjectID, determina se o objeto está em um segmento somente leitura. |
|[Método GetLOHObjectSizeThreshold](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Obtém o valor do limite de LOH configurado. |
|[Método RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs os métodos solicitados, bem como quaisquer inlineers dos métodos solicitados.  |
|[Método SuspendRuntime](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| Suspende o tempo de execução sem executar um GC. |
|[Método ResumeRuntime](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| Retoma o tempo de execução sem executar um GC. |

## <a name="requirements"></a>Requisitos  
**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
**Cabeçalho:** CorProf.idl, CorProf.h  
**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 
## <a name="see-also"></a>Consulte também
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
