---
title: Interface IXCLRDataModule
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8757642db6c4375cf55d1f7288669c4c8a752a38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790399"
---
# <a name="ixclrdatamodule-interface"></a>Interface IXCLRDataModule

Fornece métodos para consultar informações sobre um módulo carregado.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>{1&gt;Métodos&lt;1}

| Método                                                                                                                                | Descrição                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [GetMethodDefinitionByToken](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | Obtém a definição do método correspondente a um determinado token de metadados. |
| [Solicitação](ixclrdatamodule-request-method.md)                                       | Solicitações para popular o buffer fornecido com os dados do módulo.       |
| [GetVersionId](ixclrdatamodule-getversionid-method.md)                             | Obtém a ID da versão do módulo.                                       |

## <a name="remarks"></a>Comentários

Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca. No entanto, é uma interface COM que deriva de `IUnknown` com `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` de GUID que pode ser obtida por meio dos mecanismos COM usuais.

## <a name="requirements"></a>Requisitos do

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Depurando interfaces](debugging-interfaces.md)
