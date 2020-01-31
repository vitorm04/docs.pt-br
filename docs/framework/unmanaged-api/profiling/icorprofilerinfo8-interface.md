---
title: Interface ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 476bcbd91188e3ff9eb63f50cfa2118a440b1a69
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868311"
---
# <a name="icorprofilerinfo8-interface"></a>Interface ICorProfilerInfo8

Uma subclasse de [ICorProfilerInfo7](icorprofilerinfo7-interface.md) que fornece métodos para consultar informações sobre métodos dinâmicos.

## <a name="methods"></a>{1&gt;Métodos&lt;1}  

| Método|Descrição|  
| ------------|-----------------|  
|[Método IsFunctionDynamic](icorprofilerinfo8-isfunctiondynamic-method.md)| Determina se uma função não tem metadados associados.|
|[Método GetFunctionFromIP3](icorprofilerinfo8-getfunctionfromip3-method.md)| Mapeia um ponteiro de instrução de código gerenciado para uma FunctionID. Esse método funciona para métodos dinâmicos e não dinâmicos. |
|[Método GetDynamicFunctionInfo](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Recupera informações sobre métodos dinâmicos. |

## <a name="requirements"></a>Requisitos do  
**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** CorProf. idl, CorProf. h  
**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Veja também

- [Interfaces de criação de perfil](profiling-interfaces.md)
