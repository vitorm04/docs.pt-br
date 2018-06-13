---
title: ICorDebugEnum Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4659bbc9c2e3c71a6cf85e51a06bee4f789356b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422299"
---
# <a name="icordebugenum-interface1"></a>ICorDebugEnum Interface1
Serve como a interface base abstrata para os enumeradores que são usados por um aplicativo de depuração.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|Cria uma cópia deste objeto `ICorDebugEnum`.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|Obtém o número de itens na enumeração.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|Move o cursor para o início da enumeração.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|Move o cursor para a frente na enumeração pelo número especificado de itens.|  
  
## <a name="remarks"></a>Comentários  
 Os seguintes enumeradores derivam `ICorDebugEnum`:  
  
-   "ICorDebugAppDomainEnum"  
  
-   "ICorDebugAssemblyEnum"  
  
-   [ICorDebugBlockingObjectEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   "ICorDebugBreakpointEnum"  
  
-   "ICorDebugChainEnum"  
  
-   "ICorDebugCodeEnum"  
  
-   "ICorDebugErrorInfoEnum"  
  
-   [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   "ICorDebugFrameEnum"  
  
-   [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   "ICorDebugModuleEnum"  
  
-   "ICorDebugObjectEnum"  
  
-   "ICorDebugProcessEnum"  
  
-   "ICorDebugStepperEnum"  
  
-   "ICorDebugThreadEnum"  
  
-   "ICorDebugTypeEnum"  
  
-   "ICorDebugValueEnum"  
  
-   [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
