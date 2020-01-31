---
title: Método ICorDebugMDA::GetFlags
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 0c7b8dae756fbb9ab27ff187eeb83a931b016b7f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793283"
---
# <a name="icordebugmdagetflags-method"></a>Método ICorDebugMDA::GetFlags
Obtém os sinalizadores associados ao MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFlags`  
 no Uma combinação de bits bit que indica os valores de enumeração [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) que especificam as configurações dos sinalizadores para este MDA.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMDA](icordebugmda-interface.md)
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
