---
title: Método ICorDebugRemote::DebugActiveProcessEx
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e3cdbff5054ec990c40c333ed4bd4029a91f12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420798"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>Método ICorDebugRemote::DebugActiveProcessEx
Inicia um processo em um computador remoto sob o depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRemoteTarget`  
 [in] Ponteiro para um [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Esse parâmetro é usado para determinar a máquina na qual o processo está sendo executado.  
  
 `id`  
 [in] A ID do processo ao qual o depurador será anexada.  
  
 `win32Attach`  
 [in] `true` se o depurador deve se comportar conforme o depurador do Win32 para o processo e distribuir os retornos de chamada não gerenciados; caso contrário, `false`.  
  
 `ppProcess`  
 [out] Um ponteiro para o endereço de um objeto de "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 Anexado com êxito o processo no computador remoto.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 Não é possível anexar ao processo no computador remoto.  
  
## <a name="remarks"></a>Comentários  
 Não há suporte para a depuração de modo misto no Silverlight.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugRemote](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
