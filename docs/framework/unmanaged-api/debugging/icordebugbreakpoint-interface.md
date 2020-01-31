---
title: Interface ICorDebugBreakpoint
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
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784368"
---
# <a name="icordebugbreakpoint-interface"></a>Interface ICorDebugBreakpoint

Representa um ponto de interrupção em uma função ou um apontador em um valor.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Activate](icordebugbreakpoint-activate-method.md)|Define o estado ativo deste `ICorDebugBreakpoint`.|  
|[Método IsActive](icordebugbreakpoint-isactive-method.md)|Obtém um valor que indica se este `ICorDebugBreakpoint` está ativo.|  
  
## <a name="remarks"></a>Comentários  
 Os pontos de interrupção não oferecem suporte direto a expressões condicionais. Se essa funcionalidade for desejada, um depurador deverá implementá-la sobre o `ICorDebugBreakpoint`.  
  
 A interface ICorDebugFunctionBreakpoint estende `ICorDebugBreakpoint` para dar suporte a pontos de interrupção dentro de funções.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
