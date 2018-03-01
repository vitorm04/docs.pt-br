---
title: "Método ICorDebugManagedCallback2::Exception"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79a8fa4709aeb04164bd1c2da07607435b76fff5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a>Método ICorDebugManagedCallback2::Exception
Notifica o depurador que uma pesquisa para um manipulador de exceção foi iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 [in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o segmento em que a exceção foi lançada.  
  
 `pThread`  
 [in] Um ponteiro para um objeto ICorDebugThread que representa o thread em que a exceção foi lançada.  
  
 `pFrame`  
 [in] Um ponteiro para um objeto ICorDebugFrame que representa um quadro, conforme determinado pelo `dwEventType` parâmetro. Para obter mais informações, consulte a tabela na seção comentários.  
  
 `nOffset`  
 [in] Um inteiro que especifica um deslocamento, conforme determinado pelo `dwEventType` parâmetro. Para obter mais informações, consulte a tabela na seção comentários.  
  
 `dwEventType`  
 [in] Um valor da enumeração CorDebugExceptionCallbackType que especifica o tipo de retorno de chamada esta exceção.  
  
 `dwFlags`  
 [in] Um valor de [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeração que especifica informações adicionais sobre a exceção  
  
## <a name="remarks"></a>Comentários  
 O `Exception` retorno de chamada é chamado em vários pontos durante a fase de pesquisa do processo de tratamento de exceção. Ou seja, ele pode ser chamado mais de uma vez durante a liberação de uma exceção.  
  
 A exceção que está sendo processada pode ser recuperada do objeto ICorDebugThread referenciado pelo `pThread` parâmetro.  
  
 O quadro específico e o deslocamento são determinados pelo `dwEventType` parâmetro da seguinte maneira:  
  
|Valor de `dwEventType`|Valor de `pFrame`|Valor de `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|O quadro que lançou a exceção.|O ponteiro de instrução no quadro.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|O quadro de código do usuário mais próximo ao ponto da exceção lançada.|O ponteiro de instrução no quadro.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|O quadro que contém o manipulador catch.|O deslocamento de Microsoft intermediate language (MSIL) do início do manipulador catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Indefinido.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
