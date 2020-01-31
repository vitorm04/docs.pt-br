---
title: Interface ICorDebugComObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: ed5b39ed4b2a14c071bf23fb04efbad6834e8a9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783968"
---
# <a name="icordebugcomobjectvalue-interface"></a>Interface ICorDebugComObjectValue
Fornece métodos para recuperar informações associadas a um RCW (Runtime Callable Wrapper).  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetCachedInterfacePointers](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Obtém os ponteiros de interface bruto armazenados em cache no RCW atual.|  
|[Método GetCachedInterfaceTypes](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Fornece um enumerador para os tipos de interface para os quais o objeto atual foi usado em maiúsculas ou usados.|  
  
## <a name="remarks"></a>Comentários  
 Para verificar se uma instância de uma interface "ICorDebugValue" representa um RCW, um depurador chama `QueryInterface` em "ICorDebugValue" com `IID_ICorDebugComObjectValue`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
