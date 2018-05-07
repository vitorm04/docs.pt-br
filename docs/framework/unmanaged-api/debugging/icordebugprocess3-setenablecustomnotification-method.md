---
title: Método ICorDebugProcess3::SetEnableCustomNotification
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a84061cff7cc5dbdeba1e0e66396e04a8f345cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>Método ICorDebugProcess3::SetEnableCustomNotification
Ativa e desativa as notificações do depurador personalizados do tipo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pClass`  
 [in] O tipo que especifica as notificações do depurador personalizados.  
  
 `fEnable`  
 [in] `true` para habilitar as notificações do depurador personalizados; `false` para desabilitar notificações. O valor padrão é `false`.  
  
## <a name="remarks"></a>Comentários  
 Quando `fEnable` é definido como `true`, chamadas para o <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> gatilho método um [Icordebugmanagedcallback3](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) retorno de chamada. As notificações estão desabilitadas por padrão. Portanto, o depurador deve especificar quaisquer tipos de notificação, ele conhece e deseja controlar. Porque o [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) classe está no escopo do domínio de aplicativo, o depurador deve chamar `SetEnableCustomNotification` para cada domínio de aplicativo do processo se deseja receber a notificação em todo o processo.  
  
 Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], o somente de notificação com suporte é uma notificação de dependência entre threads.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
