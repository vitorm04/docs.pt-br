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
ms.openlocfilehash: 63f7bf8c09480b9ce2cfb8eb8dc66e4a6133ef8f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777482"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a>Método ICorDebugManagedCallback::ControlCTrap
Notifica o depurador de que um CTRL + C foi interceptado no processo que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pProcess`  
 no Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o CTRL + C é interceptado.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O depurador manipulará a interceptação CTRL + C.|  
|S_FALSE|O depurador não tratará a interceptação CTRL + C.|  
  
## <a name="remarks"></a>Comentários  
 Todos os domínios de aplicativo no processo são interrompidos para este retorno de chamada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
