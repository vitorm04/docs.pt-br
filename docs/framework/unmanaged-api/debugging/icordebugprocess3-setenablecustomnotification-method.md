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
ms.openlocfilehash: 58e50a0c02f15590e5bbbcadaabeaa7e3886b74b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736824"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>Método ICorDebugProcess3::SetEnableCustomNotification
Habilita e desabilita as notificações do depurador personalizados do tipo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pClass`  
 [in] O tipo que especifica as notificações do depurador personalizados.  
  
 `fEnable`  
 [in] `true` para habilitar as notificações do depurador personalizados; `false` desabilitar as notificações. O valor padrão é `false`.  
  
## <a name="remarks"></a>Comentários  
 Quando `fEnable` é definido como `true`, chamadas para o <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> gatilho de método um [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) retorno de chamada. As notificações estão desabilitadas por padrão. Portanto, o depurador deve especificar qualquer tipo de notificação, ele conhece e deseja tratar. Porque o [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) classe está no escopo por domínio de aplicativo, o depurador deve chamar `SetEnableCustomNotification` para cada domínio de aplicativo no processo de se desejam receber a notificação em todo o processo.  
  
 A notificação com suporte somente a partir do .NET Framework 4, é uma notificação de dependência entre threads.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
