---
title: Interface ICorDebugThread3
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 19bd869aec7e4d046890d2314f5142753ba0b112
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791387"
---
# <a name="icordebugthread3-interface"></a>Interface ICorDebugThread3
Fornece o ponto de entrada para o [ICorDebugStackWalk](icordebugstackwalk-interface.md) e as interfaces correspondentes.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateStackWalk](icordebugthread3-createstackwalk-method.md)|Cria um objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.|  
|[Método GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md)|Retorna uma matriz de quadros internos (objetos[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) na pilha.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugThread3` é uma extensão lógica para a interface ICorDebugThread.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
