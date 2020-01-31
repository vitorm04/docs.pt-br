---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 371e85ce8f5d7b420a30ac842ec658949e47d30e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861639"
---
# <a name="icorprofilerinfo9-interface"></a>Interface ICorProfilerInfo9

Uma subclasse de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) que fornece métodos para consultar informações sobre funções com várias versões de código nativo.  

## <a name="methods"></a>{1&gt;Métodos&lt;1}  

| Método|Descrição|  
| ------------|-----------------|  
|[Método GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md)| Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente. |
|[Método GetILToNativeMapping3](icorprofilerinfo9-getiltonativemapping3-method.md)| Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código. |
|[Método GetCodeInfo4](icorprofilerinfo9-getcodeinfo4-method.md)| Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código. |

## <a name="requirements"></a>Requisitos do  
**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**Cabeçalho:** CorProf. idl, CorProf. h  
**Versões do .net:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Veja também

- [Interfaces de criação de perfil](profiling-interfaces.md)
