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
ms.openlocfilehash: 54ef1cab27a39de39b39996729be6b8160570745
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788965"
---
# <a name="icordebugsetmanagedhandler-method"></a>Método ICorDebug::SetManagedHandler
Especifica o objeto manipulador de eventos para eventos gerenciados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCallback`  
 no Um ponteiro para um objeto [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , que é o objeto manipulador de eventos.  
  
## <a name="remarks"></a>Comentários  
 `SetManagedHandler` deve ser chamado no momento da criação.  
  
 Se a implementação de `ICorDebugManagedCallback` não contiver interfaces suficientes para lidar com eventos de depuração para o aplicativo que está sendo depurado, `SetManagedHandler` retornará um HRESULT de E_NOINTERFACE.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebug](icordebug-interface.md)
