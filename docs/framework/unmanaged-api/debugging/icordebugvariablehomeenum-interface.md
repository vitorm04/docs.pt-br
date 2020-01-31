---
title: Interface ICorDebugVariableHomeEnum
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790943"
---
# <a name="icordebugvariablehomeenum-interface"></a>Interface ICorDebugVariableHomeEnum
Fornece um enumerador para as variáveis locais e argumentos em uma função.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](icordebugvariablehomeenum-next-method.md)|Obtém o número especificado de instâncias [ICorDebugVariableHome](icordebugvariablehome-interface.md) que contêm informações sobre as variáveis e os argumentos locais em uma função.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugVariableHomeEnum` implementa a interface ICorDebugEnum.  
  
 Uma instância de `ICorDebugVariableHomeEnum` é populada com instâncias [ICorDebugVariableHome](icordebugvariablehome-interface.md) chamando o método [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) . Cada instância de [ICorDebugVariableHome](icordebugvariablehome-interface.md) na coleção representa uma variável local ou um argumento em uma função. Os objetos [ICorDebugVariableHome](icordebugvariablehome-interface.md) na coleção podem ser enumerados chamando o método [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugVariableHome](icordebugvariablehome-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
