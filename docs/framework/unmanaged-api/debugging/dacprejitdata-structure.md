---
title: Estrutura DacpReJitData
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 46031f29da6916eeaeea863ebef6924a720d7155
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793822"
---
# <a name="dacprejitdata-structure"></a>Estrutura DacpReJitData

Define as informações básicas sobre um determinado método de instrumento do criador de perfil.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a>Membros

| {1&gt;Membro&lt;1}           | Descrição                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | O número de revisão de ReJit para um método.                                                          |
| `flags`          | Um sinalizador que indica o estado atual da instrumentação ReJit do método para a versão fornecida. |
| `NativeCodeAddr` | O endereço base da implementação de rejitted do método.                                         |

## <a name="remarks"></a>Comentários

Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca. Para usá-lo, defina a estrutura conforme especificado acima. A estrutura também deve ser definida usando `ms_struct` empacotamento se não estiver usando os compiladores da Microsoft.

## <a name="requirements"></a>Requisitos do
**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Estruturas de depuração](debugging-structures.md)
