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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795684"
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

 Um membro `CorDebugStateChange` da enumeração é fornecido como um argumento quando o depurador chama `ProcessStateChanged` o método com [ICorDebugProcess4::P rocessStateChanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

 **Cabeçalho:** CorDebug.idl, CorDebug.h

 **Biblioteca:** CorGuids.lib

 **.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Declarando enumerações](debugging-enumerations.md)
- [Depuração](index.md)
