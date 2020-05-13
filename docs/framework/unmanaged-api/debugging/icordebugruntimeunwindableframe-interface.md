---
title: Interface ICorDebugRuntimeUnwindableFrame
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: a7b0608e85411844828cebea34c0ce5ef5b1bd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379381"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>Interface ICorDebugRuntimeUnwindableFrame
Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugRuntimeUnwindableFrame`é uma versão especializada da interface ICorDebugFrame. Ele é usado por métodos não gerenciados que exigem o tempo de execução para desenrolar um quadro na pilha atual. As convenções de desenrolação existentes não funcionam, pois não usam código de compilação JIT. Quando o depurador vê um quadro não-envento, ele deve usar o método [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) para desenrolar, mas deve executar a inspeção em si. Quando o depurador recebe um `ICorDebugRuntimeUnwindableFrame` , ele pode chamar o método [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) para recuperar o contexto do quadro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
