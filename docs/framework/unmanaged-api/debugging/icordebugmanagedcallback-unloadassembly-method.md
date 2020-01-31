---
title: Método ICorDebugManagedCallback::UnloadAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 06c08499298656c8314d72667d9dac88c8d11e6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788351"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a>Método ICorDebugManagedCallback::UnloadAssembly
Notifica o depurador de que um assembly Common Language Runtime foi descarregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que continha o assembly.  
  
 `pAssembly`  
 no Um ponteiro para um objeto ICorDebugAssembly que representa o assembly.  
  
## <a name="remarks"></a>Comentários  
 O assembly não deve ser usado após este retorno de chamada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método LoadAssembly](icordebugmanagedcallback-loadassembly-method.md)
- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
