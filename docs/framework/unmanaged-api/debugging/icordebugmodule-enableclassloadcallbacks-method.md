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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec9b4867ad19f25e35ca31c007c0d238b949abab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762218"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>Método ICorDebugModule::EnableClassLoadCallbacks
Controles se o [icordebugmanagedcallback:: loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) retornos de chamada são chamados para esse módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bClassLoadCallbacks`  
 [in] Defina esse valor como `true` para habilitar o common language runtime (CLR) para chamar o `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` métodos quando ocorrem os eventos associados.  
  
 O valor padrão é `false` para os módulos não dinâmicos. O valor é sempre `true` para módulos dinâmicos e não pode ser alterado.  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` retornos de chamada estão sempre habilitados para módulos dinâmicos e não pode ser desabilitados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
