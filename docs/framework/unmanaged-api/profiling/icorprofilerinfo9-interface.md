---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 431a546fb4a3b92b379e273553f0caf540ba1473
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449720"
---
# <a name="icorprofilerinfo9-interface"></a>Interface ICorProfilerInfo9

Uma subclasse de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) que fornece métodos para consultar informações sobre funções com várias versões de código nativo.  

## <a name="methods"></a>Métodos  

| Método|DESCRIÇÃO|  
| ------------|-----------------|  
|[Método GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md)| Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente. |
|[Método GetILToNativeMapping3](icorprofilerinfo9-getiltonativemapping3-method.md)| Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código. |
|[Método GetCodeInfo4](icorprofilerinfo9-getcodeinfo4-method.md)| Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código. |

## <a name="requirements"></a>Requisitos  
**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?pivots=os-windows).  
**Cabeçalho:** CorProf. idl, CorProf. h  
**Versões do .net:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Confira também

- [Interfaces de criação de perfil](profiling-interfaces.md)
