---
title: Método ICorDebug::CanLaunchOrAttach
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 354df02b27e87550ba602fe102352455c227441b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859678"
---
# <a name="icordebugcanlaunchorattach-method"></a>Método ICorDebug::CanLaunchOrAttach
Retorna um HRESULT que indica se é possível iniciar um novo processo ou anexar ao processo existente especificado no contexto da configuração atual do computador e do tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwProcessId`  
 no A ID de um processo existente.  
  
 `win32DebuggingEnabled`  
 no Passe `true` se você planeja iniciar com a depuração do Win32 habilitada ou para anexar com a depuração do Win32 habilitada; caso contrário, `false`passe.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se os serviços de depuração determinarem que a inicialização de um novo processo ou a anexação ao processo fornecido é possível, dadas as informações sobre o computador atual e a configuração de tempo de execução. Os possíveis valores HRESULT são:  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Comentários  
 Esse método é puramente informativo. A interface não o impedirá de iniciar ou anexar a um processo, independentemente do valor retornado por `CanLaunchOrAttach`.  
  
 Se você planeja iniciar com a depuração do Win32 habilitada ou anexada à depuração do `true` Win32 `win32DebuggingEnabled`habilitada, passe para. O HRESULT retornado por `CanLaunchOrAttach` pode ser diferente se você usar essa opção.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebug](icordebug-interface.md)
