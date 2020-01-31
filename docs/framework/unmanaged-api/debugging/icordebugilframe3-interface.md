---
title: Interface ICorDebugILFrame3
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: 739c648173d45a9c147ea2a4e469a3a4b518e893
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794342"
---
# <a name="icordebugilframe3-interface"></a>Interface ICorDebugILFrame3
Fornece um método que encapsula o valor de retorno de uma função. `ICorDebugILFrame3` é uma extensão lógica das interfaces ICorDebugILFrame e ICorDebugILFrame2.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)|Obtém um objeto ICorDebugValue que encapsula o valor de retorno de uma função.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugCode3](icordebugcode3-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
