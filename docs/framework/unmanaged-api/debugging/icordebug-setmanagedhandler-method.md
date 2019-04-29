---
title: Método ICorDebug::SetManagedHandler
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f30089879f2d023c8fb04b52e75b2942da2a83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786341"
---
# <a name="icordebugsetmanagedhandler-method"></a>Método ICorDebug::SetManagedHandler
Especifica o objeto de manipulador de eventos para eventos gerenciados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCallback`  
 [in] Um ponteiro para um [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objeto, que é o objeto de manipulador de eventos.  
  
## <a name="remarks"></a>Comentários  
 `SetManagedHandler` deve ser chamado no momento da criação.  
  
 Se o `ICorDebugManagedCallback` a implementação não contêm interfaces suficientes para lidar com eventos de depuração para o aplicativo que está sendo depurado, `SetManagedHandler` retorna um HRESULT de E_NOINTERFACE.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
