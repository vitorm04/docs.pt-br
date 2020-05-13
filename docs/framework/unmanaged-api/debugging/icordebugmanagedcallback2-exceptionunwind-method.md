---
title: Método ICorDebugManagedCallback2::ExceptionUnwind
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 8f66369d3ac5ddcfe38fe579cac728eb3a250165
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205621"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>Método ICorDebugManagedCallback2::ExceptionUnwind
Fornece uma notificação de status durante o processo de desenrolamento de exceções.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread no qual a exceção foi gerada.  
  
 `pThread`  
 no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual a exceção foi gerada.  
  
 `dwEventType`  
 no Um valor da enumeração CorDebugExceptionUnwindCallbackType que especifica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.  
  
 `dwFlags`  
 no Um valor da enumeração [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) que especifica informações adicionais sobre a exceção.  
  
## <a name="remarks"></a>Comentários  
 `ExceptionUnwind`é chamado em vários pontos durante a fase de desenrolamento do processo de tratamento de exceção. `ExceptionUnwind`pode ser chamado mais de uma vez ao desenrolar uma única exceção.  
  
 Se `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, o ponteiro de instrução estará no quadro folha do thread, no ponto de sequência antes (isso pode ser várias instruções antes) a instrução que levou à exceção.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)
- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
