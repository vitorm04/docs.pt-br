---
title: Estrutura CLRDATA_IL_ADDRESS_MAP
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179372"
---
# <a name="clrdata_il_address_map-structure"></a>Estrutura CLRDATA_IL_ADDRESS_MAP

Define um IL para endereçar mapeamento.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a>Membros

| Membro         | Descrição                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | Deslocamento il para a faixa de endereço contida              |
| `startAddress` | O endereço inicial do intervalo.                        |
| `endAddress`   | O endereço final do intervalo.                          |
| `type`         | O tipo de dados. Este valor não é usado no momento |

## <a name="remarks"></a>Comentários

Esta estrutura vive dentro do tempo de execução e não é exposta através de nenhum cabeçalho ou arquivos de biblioteca. Para usá-lo, defina a estrutura `CLRDATA_ADDRESS` como especificado acima, onde está um inteiro não assinado de 64 bits.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhuma **versão framework .NET:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Confira também

- [Enumeração CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Depuração](index.md)
- [Estruturas de depuração](debugging-structures.md)
