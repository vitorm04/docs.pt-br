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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f86cc83936dd8150ca6b3f28c9b6a624278e2b36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcanlaunchorattach-method"></a>Método ICorDebug::CanLaunchOrAttach
Retorna um HRESULT que indica se iniciar um novo processo ou anexar ao processo existente especificado é possíveis dentro do contexto da configuração do computador e o tempo de execução atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwProcessId`  
 [in] A ID de um processo existente.  
  
 `win32DebuggingEnabled`  
 [in] Passar `true` se você planeja iniciar com Win32 depuração habilitada ou anexar com Win32 depuração habilitada; caso contrário, passe `false`.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se os serviços de depuração determinam que iniciar um novo processo ou anexar ao processo determinado é possível, as informações sobre a configuração de máquina e tempo de execução atual. Os valores HRESULT possíveis são:  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Comentários  
 Esse método é meramente informativo. A interface não irá parar de iniciar ou anexar a um processo, independentemente do valor retornado por `CanLaunchOrAttach`.  
  
 Se você planeja iniciar com Win32 depuração habilitada ou anexar com Win32 depuração habilitada, transmitir `true` para `win32DebuggingEnabled`. O HRESULT retornado pelo `CanLaunchOrAttach` pode ser diferente se você usar essa opção.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
