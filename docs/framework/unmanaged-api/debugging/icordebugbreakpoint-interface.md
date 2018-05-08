---
title: ICorDebugBreakpoint Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 220cd1a41ed69325b557e6498a511865b78817ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugbreakpoint-interface1"></a>ICorDebugBreakpoint Interface1
Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Activate](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|Define o estado ativo deste `ICorDebugBreakpoint`.|  
|[Método IsActive](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|Obtém um valor que indica se este `ICorDebugBreakpoint` está ativa.|  
  
## <a name="remarks"></a>Comentários  
 Pontos de interrupção não dão suporte diretamente a expressões condicionais. Se essa funcionalidade é desejada, um depurador deve implementar a ele na parte superior do `ICorDebugBreakpoint`.  
  
 Estende a interface ICorDebugFunctionBreakpoint `ICorDebugBreakpoint` para dar suporte a pontos de interrupção em funções.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
