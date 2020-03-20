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
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178369"
---
# <a name="ixclrdataprocess-interface"></a>Interface IXCLRDataProcess

Fornece métodos para consultar informações sobre um processo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Métodos

| Método                                                                                                                                               | Descrição                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Recebe `AppDomain` um em um processo por sua identificação única.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Fornece uma alça para enumerar os módulos de um processo.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Enumera os módulos desse processo.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Libera os recursos utilizados pelos ativadores internos utilizados durante a enumeração do módulo.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Fornece uma alça para enumerar `AppDomain` as instâncias do método de começar em um determinado endereço. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Enumera as instâncias de método deste processo a partir de uma compensação de endereço.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Libera os recursos utilizados pelos ativadores internos usados durante a enumeração da instância.             |

## <a name="remarks"></a>Comentários

Esta interface vive dentro do tempo de execução e não é exposta através de nenhum cabeçalho ou arquivos de biblioteca. No entanto, é uma interface `IUnknown` COM `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` que deriva de com GUID que pode ser obtida através dos mecanismos COM usuais.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Confira também

- [Depuração](index.md)
- [Depurando interfaces](debugging-interfaces.md)
