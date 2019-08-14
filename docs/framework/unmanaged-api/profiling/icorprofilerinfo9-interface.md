---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 0ba4f2b4a515143d50bc812f04ea75d821b69471
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973796"
---
# <a name="icorprofilerinfo9-interface"></a>Interface ICorProfilerInfo9

Uma subclasse de [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) que fornece métodos para consultar informações sobre funções com várias versões de código nativo.  

## <a name="methods"></a>Métodos  

| Método|Descrição|  
| ------------|-----------------|  
|[Método GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente. |
|[Método GetILToNativeMapping3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código. |
|[Método GetCodeInfo4](icorprofilerinfo9-getcodeinfo4-method.md)| Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código. |

## <a name="requirements"></a>Requisitos  
**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
**Cabeçalho:** CorProf.idl, CorProf.h  
**Versões do .net:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  
## <a name="see-also"></a>Consulte também
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
