---
title: Método ICorDebugModule::EnableClassLoadCallbacks
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139213"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>Método ICorDebugModule::EnableClassLoadCallbacks
Controla se os retornos de chamada [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) são chamados para este módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bClassLoadCallbacks`  
 no Defina esse valor como `true` para habilitar o Common Language Runtime (CLR) para chamar os métodos `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` quando seus eventos associados ocorrerem.  
  
 O valor padrão é `false` para módulos não dinâmicos. O valor sempre é `true` para módulos dinâmicos e não pode ser alterado.  
  
## <a name="remarks"></a>Comentários  
 Os retornos de chamada `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` estão sempre habilitados para módulos dinâmicos e não podem ser desabilitados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
