---
title: ISOSDacInterface Interface
ms.date: 01/16/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5e037cf6fb88fff4886733ff4152dca0a827e0a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491022"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface Interface

Fornece métodos auxiliares para acessar dados de `SOS`.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Métodos

| Método                                                                                                               | Descrição                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | Obtém os dados para o determinado [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md). |

## <a name="remarks"></a>Comentários

Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca. No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` que pode ser obtido por meio de mecanismos COM usual.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Consulte também

- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
