---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175064"
---
# <a name="icorprofilerinfo10-interface"></a>Interface ICorProfilerInfo10

Uma subclasse do [ICorProfilerInfo9](icorprofilerinfo9-interface.md) que fornece métodos para modificar a função IL, consultar informações a partir do tempo de execução e suspender e retomar o tempo de execução.

## <a name="methods"></a>Métodos  

| Método|Descrição|  
| ------------|-----------------|  
|[Método EnumerateObjectReferences](icorprofilerinfo10-enumerateobjectreferences-method.md)|Dado um ObjectID, callback e clientData, enumera cada referência de objeto (se houver). |
|[Método IsFrozenObject](icorprofilerinfo10-isfrozenobject-method.md)|Dado um ObjectID, determina se o objeto está em um segmento somente leitura. |
|[Método GetLOHObjectSizeThreshold](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Obtém o valor do limite LOH configurado. |
|[Método RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs os métodos solicitados, bem como quaisquer inliners dos métodos solicitados.  |
|[Método SuspendRuntime](icorprofilerinfo10-suspendruntime-method.md)| Suspende o tempo de execução sem realizar um GC. |
|[Método ResumeRuntime](icorprofilerinfo10-resumeruntime-method.md)| Retoma o tempo de execução sem realizar um GC. |

## <a name="requirements"></a>Requisitos  
**Plataformas:** Consulte [os sistemas operacionais suportados pelo .NET Core](../../../core/install/dependencies.md?pivots=os-windows).  
**Cabeçalho:** CorProf.idl, CorProf.h  
**.NET Versões:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Confira também

- [Criação de perfil de interfaces](profiling-interfaces.md)
