---
title: Interface ICorDebugGuidToTypeEnum
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: 2663e5604cdd55472cc148b2d2b38599df81f11e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794447"
---
# <a name="icordebugguidtotypeenum-interface"></a>Interface ICorDebugGuidToTypeEnum
Fornece um enumerador que define o mapeamento entre um conjunto de GUIDs e seus tipos correspondentes, que são representados por instâncias de ICorDebugType. Essa interface herda os métodos da interface ICorDebugEnum.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum::Next](icordebugguidtotypeenum-next-method.md)|Obtém o número especificado de instâncias de [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) que MAPEIAm GUIDs para informações de tipo.|  
  
## <a name="remarks"></a>Comentários  
 Um objeto de interface `ICorDebugGuidToTypeEnum` pode ser recuperado chamando o método [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) . Um depurador pode chamar o [próximo](icordebugguidtotypeenum-next-method.md) método da interface para recuperar objetos [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) que representam mapeamentos de representações gerenciadas de tipos de Windows Runtime carregados no domínio de aplicativo usado para a chamada para o método [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** Windows Runtime  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
