---
title: Método ICorDebugExceptionDebugEvent::GetStackPointer
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9d4c0a1938edd3e2fe88ea6e418b3430f1b5cb8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163196"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>Método ICorDebugExceptionDebugEvent::GetStackPointer
Obtém o ponteiro de pilha para esse evento de depuração de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pStackPointer`  
 [out] Evento de depuração de um ponteiro para o endereço do ponteiro de pilha para essa exceção. Consulte a seção Comentários para obter mais informações.  
  
## <a name="remarks"></a>Comentários  
 O significado deste ponteiro de pilha depende do tipo de evento, conforme mostrado na tabela a seguir.  
  
|Tipo de evento|Significado do `pStackPointer` valor|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|O ponteiro de pilha para o quadro que gerou a exceção.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|O ponteiro de pilha para o quadro de código do usuário mais próximo ao ponto da exceção lançada.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|O ponteiro de pilha para o quadro que contém o manipulador catch.|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pStackPointer` is **null**.|  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
 O tipo de evento é proveniente de [icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
