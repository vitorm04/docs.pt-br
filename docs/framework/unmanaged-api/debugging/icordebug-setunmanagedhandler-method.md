---
title: Método ICorDebug::SetUnmanagedHandler
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: cafa1c99a8988c199d866796911d1983aabb7208
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785060"
---
# <a name="icordebugsetunmanagedhandler-method"></a>Método ICorDebug::SetUnmanagedHandler
Especifica o objeto do manipulador de eventos para eventos não gerenciados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCallback`  
 no Um ponteiro para um objeto [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) que representa o manipulador de eventos para eventos não gerenciados.  
  
## <a name="remarks"></a>Comentários  
 O objeto manipulador de eventos para eventos não gerenciados deve ser definido após uma chamada para [ICorDebug:: Initialize](icordebug-initialize-method.md) e antes de qualquer chamada para [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) ou [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md). No entanto, para fins herdados, não é necessário definir o objeto manipulador de eventos para eventos não gerenciados até que o primeiro evento de depuração nativa seja gerado. Especificamente, se `ICorDebug::CreateProcess` tiver definido o sinalizador CREATE_SUSPENDED, os eventos de depuração nativos não poderão ser expedidos até que o thread principal seja retomado.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebug](icordebug-interface.md)
