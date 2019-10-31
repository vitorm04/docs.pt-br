---
title: Enumeração CorDebugStateChange
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133718"
---
# <a name="cordebugstatechange-enumeration"></a>Enumeração CorDebugStateChange

Descreve a quantidade de dados armazenados em cache que devem ser descartados com base em alterações no processo.

## <a name="syntax"></a>Sintaxe

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>Membros

| Membro            | Descrição                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | O processo atingiu um novo estado de memória por meio da execução do encaminhamento.            |
| `FLUSH_ALL`       | A memória do processo pode ser arbitrariamente diferente do que era anteriormente. |

## <a name="remarks"></a>Comentários

 Um membro da enumeração `CorDebugStateChange` é fornecido como um argumento quando o depurador chama o método `ProcessStateChanged` com [ICorDebugProcess4::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

 **Cabeçalho:** CorDebug.idl, CorDebug.h

 **Biblioteca:** CorGuids.lib

 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Declarando enumerações](debugging-enumerations.md)
- [Depuração](index.md)
