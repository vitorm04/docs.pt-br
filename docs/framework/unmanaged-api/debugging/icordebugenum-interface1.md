---
title: Interface ICorDebugEnum
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: 7575be3f5074243b251c80b8dd5bdbb12e5d50fd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976312"
---
# <a name="icordebugenum-interface"></a>Interface ICorDebugEnum

Serve como a interface base abstrata para os enumeradores que são usados por um aplicativo de depuração.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](icordebugenum-clone-method.md)|Cria uma cópia deste objeto `ICorDebugEnum`.|  
|[Método GetCount](icordebugenum-getcount-method.md)|Obtém o número de itens na enumeração.|  
|[Método Reset](icordebugenum-reset-method.md)|Move o cursor para o início da enumeração.|  
|[Método Skip](icordebugenum-skip-method.md)|Move o cursor para a frente na enumeração pelo número especificado de itens.|  
  
## <a name="remarks"></a>Comentários  
 Os seguintes enumeradores derivam `ICorDebugEnum`de:  
  
- "ICorDebugAppDomainEnum"  
  
- "ICorDebugAssemblyEnum"  
  
- [ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)  
  
- "ICorDebugBreakpointEnum"  
  
- "ICorDebugChainEnum"  
  
- "ICorDebugCodeEnum"  
  
- "ICorDebugErrorInfoEnum"  
  
- [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)  
  
- "ICorDebugFrameEnum"  
  
- [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)  
  
- [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)  
  
- [ICorDebugHeapEnum](icordebugheapenum-interface.md)  
  
- [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)  
  
- "ICorDebugModuleEnum"  
  
- "ICorDebugObjectEnum"  
  
- "ICorDebugProcessEnum"  
  
- "ICorDebugStepperEnum"  
  
- "ICorDebugThreadEnum"  
  
- "ICorDebugTypeEnum"  
  
- "ICorDebugValueEnum"  
  
- [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](debugging-interfaces.md)
