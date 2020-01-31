---
title: Interface IXCLRDataProcess
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790368"
---
# <a name="ixclrdataprocess-interface"></a>Interface IXCLRDataProcess

Fornece métodos para consultar informações sobre um processo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>{1&gt;Métodos&lt;1}

| Método                                                                                                                                               | Descrição                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Obtém um `AppDomain` em um processo por sua ID exclusiva.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Fornece um identificador para enumerar os módulos de um processo.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Enumera os módulos desse processo.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Libera os recursos usados por iteradores internos usados durante a enumeração do módulo.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Fornece um identificador para enumerar as instâncias de método de `AppDomain` a partir de um determinado endereço. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Enumera as instâncias de método deste processo Iniciando em um deslocamento de endereço.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Libera os recursos usados por iteradores internos usados durante a enumeração da instância.             |

## <a name="remarks"></a>Comentários

Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca. No entanto, é uma interface COM que deriva de `IUnknown` com `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` de GUID que pode ser obtida por meio dos mecanismos COM usuais.

## <a name="requirements"></a>Requisitos do

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).   
**Cabeçalho:** None  
**Biblioteca:** None  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Depurando interfaces](debugging-interfaces.md)
