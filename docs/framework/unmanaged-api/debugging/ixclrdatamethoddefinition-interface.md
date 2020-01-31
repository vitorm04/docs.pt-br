---
title: Interface IXCLRDataMethodDefinition
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790422"
---
# <a name="ixclrdatamethoddefinition-interface"></a>Interface IXCLRDataMethodDefinition

Fornece métodos para consultar informações sobre uma definição de método.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>{1&gt;Métodos&lt;1}

Os métodos a seguir são alguns dos métodos disponíveis na interface.

| Método                                                                                                                          | Descrição                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [StartEnumInstances](ixclrdatamethoddefinition-startenuminstances-method.md) | Fornece um identificador para a enumeração de instâncias de método para um determinado `IXCLRDataAppDomain`. |
| [EnumInstance](ixclrdatamethoddefinition-enuminstance-method.md)             | Enumera as instâncias desta definição de método.                                         |
| [EndEnumInstances](ixclrdatamethoddefinition-endenuminstances-method.md)     | Libera os recursos usados por iteradores internos usados durante a enumeração da instância.         |

## <a name="remarks"></a>Comentários

Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca. No entanto, é uma interface COM que deriva de `IUnknown` com `AAF60008-FB2C-420b-8FB1-42D244A54A97` de GUID que pode ser obtida por meio dos mecanismos COM usuais.

## <a name="requirements"></a>Requisitos do

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Depurando interfaces](debugging-interfaces.md)
