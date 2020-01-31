---
title: Interface ICorDebugHeapSegmentEnum
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: 98e3351c9c86961d11b0985117259d0ff3b609ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794414"
---
# <a name="icordebugheapsegmentenum-interface"></a>Interface ICorDebugHeapSegmentEnum
Fornece um enumerador para regiões de memória do heap gerenciado. Essa interface é uma subclasse da interface ICorDebugEnum.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](icordebugheapsegmentenum-next-method.md)|Obtém o número especificado de instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) que contêm informações sobre regiões do heap gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugHeapSegmentEnum` implementa a interface ICorDebugEnum.  
  
 Uma instância de `ICorDebugHeapSegmentEnum` é populada com instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) chamando o método [ICorDebugProcess5:: EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) . Os objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) na coleção podem ser enumerados chamando o método [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) .  
  
 Um objeto de coleção de `ICorDebugHeapSegmentEnum` enumera todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados realmente residam nessas regiões. Ele pode incluir informações sobre regiões de memória vazias ou reservadas.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
