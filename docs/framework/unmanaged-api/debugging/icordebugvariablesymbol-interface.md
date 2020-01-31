---
title: Interface ICorDebugVariableSymbol
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 9d17bc92dcae9e906dfe18d7665fbf489d278234
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790867"
---
# <a name="icordebugvariablesymbol-interface"></a>Interface ICorDebugVariableSymbol
Recupera as informações de símbolo de depuração para uma variável.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetName](icordebugvariablesymbol-getname-method.md)|Obtém o nome de uma variável.|  
|[Método GetSize](icordebugvariablesymbol-getsize-method.md)|Obtém o tamanho de uma variável em bytes.|  
|[Método GetSlotIndex](icordebugvariablesymbol-getslotindex-method.md)|Obtém o índice de slot gerenciado de uma variável local.|  
|[Método GetValue](icordebugvariablesymbol-getvalue-method.md)|Obtém o valor de uma variável como uma matriz de bytes.|  
|[Método SetValue](icordebugvariablesymbol-setvalue-method.md)|Atribui o valor de uma matriz de bytes a uma variável.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Essa interface está disponível somente com .NET Native. Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
