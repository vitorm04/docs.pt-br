---
title: Método ICorDebugManagedCallback::ControlCTrap
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f4794fb0383435f828626497036ad3458df2173
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995326"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a>Método ICorDebugManagedCallback::ControlCTrap
Notifica o depurador que um CTRL + C é interceptado no processo que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o CTRL + C é interceptada.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O depurador irá manipular a interceptação CTRL + C.|  
|S_FALSE|O depurador não manipulará a interceptação CTRL + C.|  
  
## <a name="remarks"></a>Comentários  
 Todos os domínios de aplicativo dentro do processo são interrompidos para esse retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
