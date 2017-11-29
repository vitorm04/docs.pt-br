---
title: "Método ICorDebugExceptionDebugEvent::GetNativeIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 616f0a9787220aba0cc4d460c80b856076e1e437
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>Método ICorDebugExceptionDebugEvent::GetNativeIP
Obtém o ponteiro de instrução nativo para este evento de depuração de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pIP`  
 [out] Eventos de depuração de um ponteiro para o ponteiro de instrução para essa exceção. Consulte a seção Comentários para obter mais informações.  
  
## <a name="remarks"></a>Comentários  
 O significado deste ponteiro de instrução depende do tipo de evento, conforme mostrado na tabela a seguir.  
  
|Tipo de evento|Significado da `pStackPointer` valor|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|O endereço da instrução com falha.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|O endereço de código no quadro indicado pelo [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) método em que a execução será retomada se nenhuma exceção tivesse sido gerada. A exceção podem ou não pode causar um código diferente, como o bloco catch de uma `try/catch/finally` cláusula, para ser executado nesse quadro.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|O código de endereço onde `catch` será iniciar a execução do manipulador no quadro indicado pelo [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) método.|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pIP` é 0.|  
  
 O tipo de evento é proveniente do [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
