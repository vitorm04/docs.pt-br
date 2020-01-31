---
title: Método ICorDebugManagedCallback::UnloadModule
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: 88ef9fd5a0aac19954a247d0215fe698ebe30d40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788330"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a>Método ICorDebugManagedCallback::UnloadModule
Notifica o depurador de que um módulo de Common Language Runtime (DLL) foi descarregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que continha o módulo.  
  
 `pModule`  
 no Um ponteiro para um objeto ICorDebugModule que representa o módulo.  
  
## <a name="remarks"></a>Comentários  
 O módulo não deve ser usado após esta chamada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método LoadModule](icordebugmanagedcallback-loadmodule-method.md)
- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
