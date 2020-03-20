---
title: ICorDebugProcess4::ProcessStateChanged Method
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178637"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::ProcessStateChanged Method

Notifica o pipeline ICorDebug de que o depurador fora de processo continua a execução do depurador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>parâmetros

 `eChange`\
[em] Um membro da [enumeração CorDebugStateChange](cordebugstatechange-enumeration.md) descrevendo uma mudança no estado de execução do processo.

## <a name="remarks"></a>Comentários

O método fornecido faz `ICorDebugProcess4` parte da interface e corresponde ao quarto slot da tabela de métodos virtuais.

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

 **Cabeçalho:** Nenhum

 **Biblioteca:** Nenhum

 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Confira também

- [Interface ICorDebugProcess4](icordebugprocess4-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
