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
ms.openlocfilehash: b95e9f3a0d584511a2bcf156ed2c50a98f96d071
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379056"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>Método ICorDebugRemote::DebugActiveProcessEx
Inicia um processo em um computador remoto sob o depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pRemoteTarget`  
 no Ponteiro para uma [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md). Esse parâmetro é usado para determinar o computador no qual o processo está em execução.  
  
 `id`  
 no A ID do processo ao qual o depurador deve ser anexado.  
  
 `win32Attach`  
 [in] `true` Se o depurador deve se comportar como o depurador do Win32 para o processo e expedir os retornos de chamada não gerenciados; caso contrário, `false` .  
  
 `ppProcess`  
 fora Um ponteiro para o endereço de um objeto "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK  
 Anexado com êxito ao processo no computador remoto.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 Não é possível anexar ao processo no computador remoto.  
  
## <a name="remarks"></a>Comentários  
 Não há suporte para a depuração de modo misto no Silverlight.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugRemote](icordebugremote-interface.md)
- [Interface ICorDebug](icordebug-interface.md)

- [Depurando interfaces](debugging-interfaces.md)
