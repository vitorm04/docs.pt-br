---
title: Enumeração CorDebugExceptionCallbackType
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: 977b1608539a302c6a27a1b54cfb2ad687025fe6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789417"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a>Enumeração CorDebugExceptionCallbackType
Indica o tipo de retorno de chamada que é feito de um evento [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|Uma exceção foi lançada.|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|O processo de windup de exceção inseriu o código do usuário.|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|O processo de windup de exceção encontrou um bloco de `catch` no código do usuário.|  
|`DEBUG_EXCEPTION_UNHANDLED`|A exceção não foi tratada.|  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Declarando enumerações](debugging-enumerations.md)
