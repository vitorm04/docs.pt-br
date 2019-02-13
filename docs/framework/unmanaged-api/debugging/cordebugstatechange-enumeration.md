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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05a29022d3ebad37322aef9826f10689d2b5b06b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221128"
---
# <a name="cordebugstatechange-enumeration"></a>Enumeração CorDebugStateChange

Descreve a quantidade de dados armazenados em cache que devem ser descartados com base em alterações no processo.

## <a name="syntax"></a>Sintaxe

```
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

 Um membro do `CorDebugStateChange` enumeração é fornecida como um argumento quando o depurador chama o `ProcessStateChanged` método com [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Requisitos

 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

 **Cabeçalho:** CorDebug.idl, CorDebug.h

 **Biblioteca:** CorGuids.lib

 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Declarando enumerações](debugging-enumerations.md)
- [Depuração](index.md)
