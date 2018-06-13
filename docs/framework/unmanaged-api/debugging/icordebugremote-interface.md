---
title: Interface ICorDebugRemote
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab8ed5c4fa3dc0ed77c1948aa6c1b940ecc25c14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421445"
---
# <a name="icordebugremote-interface"></a>Interface ICorDebugRemote
Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ICorDebugRemote::CreateProcessEx](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|Cria um processo em um computador remoto para depuração gerenciada.|  
|[Método ICorDebugRemote::DebugActiveProcessEx](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|Inicia um processo em um computador remoto sob o depurador.|  
  
## <a name="remarks"></a>Comentários  
 Atualmente, essa funcionalidade tem suporte somente para um destino de aplicativo baseado em Silverlight que está em execução em um computador Macintosh remoto de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
