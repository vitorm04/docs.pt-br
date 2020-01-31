---
title: Método ICorDebugManagedCallback::ExitThread
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: fa649fd1983a76c71d400ad3e6965ac0794da6ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781603"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a>Método ICorDebugManagedCallback::ExitThread
Notifica o depurador de que um thread que estava executando código gerenciado foi encerrado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado.  
  
 `thread`  
 no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Depois que o retorno de chamada `ExitThread` for disparado, o thread não aparecerá mais nas enumerações de thread.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
