---
title: Método ICorDebugManagedCallback::LoadModule
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 21a97f140a41f8f380c1334652bc2417e19659c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777131"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>Método ICorDebugManagedCallback::LoadModule
Notifica o depurador de que um módulo Common Language Runtime (CLR) foi carregado com êxito.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual o módulo foi carregado.  
  
 `pModule`  
 no Um ponteiro para um objeto ICorDebugModule que representa o módulo CLR.  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada `LoadModule` fornece um tempo apropriado para examinar os metadados do módulo, definir sinalizadores de compilador JIT (just-in-time) ou habilitar ou desabilitar retornos de chamada de carregamento de classe para o módulo.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método UnloadModule](icordebugmanagedcallback-unloadmodule-method.md)
- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
