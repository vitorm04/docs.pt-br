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
ms.openlocfilehash: 0a5a87c71bea603073c35dd851e443ca8c497523
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210430"
---
# <a name="icordebugheapsegmentenum-interface"></a>Interface ICorDebugHeapSegmentEnum
Fornece um enumerador para regiões de memória do heap gerenciado. Essa interface é uma subclasse da interface ICorDebugEnum.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](icordebugheapsegmentenum-next-method.md)|Obtém o número especificado de instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) que contêm informações sobre regiões do heap gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 A `ICorDebugHeapSegmentEnum` interface implementa a interface ICorDebugEnum.  
  
 Uma `ICorDebugHeapSegmentEnum` instância é populada com instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) chamando o método [ICorDebugProcess5:: EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) . Os objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) na coleção podem ser enumerados chamando o método [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) .  
  
 Um `ICorDebugHeapSegmentEnum` objeto de coleção enumera todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados realmente residam nessas regiões. Ele pode incluir informações sobre regiões de memória vazias ou reservadas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
