---
title: Método ICorDebugManagedCallback2::Exception
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: f40030a2034057e83de51a21655a686f30b9ee88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137451"
---
# <a name="icordebugmanagedcallback2exception-method"></a>Método ICorDebugManagedCallback2::Exception
Notifica o depurador de que uma pesquisa de um manipulador de exceção foi iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread no qual a exceção foi gerada.  
  
 `pThread`  
 no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual a exceção foi gerada.  
  
 `pFrame`  
 no Um ponteiro para um objeto ICorDebugFrame que representa um quadro, conforme determinado pelo parâmetro `dwEventType`. Para obter mais informações, consulte a tabela na seção comentários.  
  
 `nOffset`  
 no Um inteiro que especifica um deslocamento, conforme determinado pelo parâmetro `dwEventType`. Para obter mais informações, consulte a tabela na seção comentários.  
  
 `dwEventType`  
 no Um valor da enumeração CorDebugExceptionCallbackType que especifica o tipo deste retorno de chamada de exceção.  
  
 `dwFlags`  
 no Um valor da enumeração [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) que especifica informações adicionais sobre a exceção  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada `Exception` é chamado em vários pontos durante a fase de pesquisa do processo de tratamento de exceção. Ou seja, ele pode ser chamado mais de uma vez ao desenrolar uma exceção.  
  
 A exceção que está sendo processada pode ser recuperada do objeto ICorDebugThread referenciado pelo parâmetro `pThread`.  
  
 O quadro e o deslocamento específicos são determinados pelo parâmetro `dwEventType` da seguinte maneira:  
  
|Valor de `dwEventType`|Valor de `pFrame`|Valor de `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|O quadro que gerou a exceção.|O ponteiro de instrução no quadro.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|O quadro de código do usuário mais próximo do ponto da exceção gerada.|O ponteiro de instrução no quadro.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|O quadro que contém o manipulador catch.|O deslocamento da MSIL (Microsoft Intermediate Language) do início do manipulador catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Indefinido.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
