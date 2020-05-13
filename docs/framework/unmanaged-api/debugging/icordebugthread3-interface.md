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
ms.openlocfilehash: dc556dfb59e999ed9b7fc5f35c603dc26c35f314
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378715"
---
# <a name="icordebugthread3-interface"></a>Interface ICorDebugThread3
Fornece o ponto de entrada para o [ICorDebugStackWalk](icordebugstackwalk-interface.md) e as interfaces correspondentes.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateStackWalk](icordebugthread3-createstackwalk-method.md)|Cria um objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.|  
|[Método GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md)|Retorna uma matriz de quadros internos (objetos[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) na pilha.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugThread3`é uma extensão lógica para a interface ICorDebugThread.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
