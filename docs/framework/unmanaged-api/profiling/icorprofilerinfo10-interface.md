---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: e90a1ffbc037636e4296bbd4f4c3c5082885e9f3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863238"
---
# <a name="icorprofilerinfo10-interface"></a>Interface ICorProfilerInfo10

Uma subclasse de [ICorProfilerInfo9](icorprofilerinfo9-interface.md) que fornece métodos para modificar o Il da função, consultar informações do tempo de execução e suspender e retomar o tempo de execução.

## <a name="methods"></a>{1&gt;Métodos&lt;1}  

| Método|Descrição|  
| ------------|-----------------|  
|[Método EnumerateObjectReferences](icorprofilerinfo10-enumerateobjectreferences-method.md)|Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver). |
|[Método iscongeladoobject](icorprofilerinfo10-isfrozenobject-method.md)|Dado um ObjectID, determina se o objeto está em um segmento somente leitura. |
|[Método GetLOHObjectSizeThreshold](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Obtém o valor do limite de LOH configurado. |
|[Método RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs os métodos solicitados, bem como quaisquer inlineers dos métodos solicitados.  |
|[Método SuspendRuntime](icorprofilerinfo10-suspendruntime-method.md)| Suspende o tempo de execução sem executar um GC. |
|[Método ResumeRuntime](icorprofilerinfo10-resumeruntime-method.md)| Retoma o tempo de execução sem executar um GC. |

## <a name="requirements"></a>Requisitos do  
**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**Cabeçalho:** CorProf. idl, CorProf. h  
**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>Veja também

- [Interfaces de criação de perfil](profiling-interfaces.md)
