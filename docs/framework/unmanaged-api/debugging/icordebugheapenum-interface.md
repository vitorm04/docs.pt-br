---
title: Interface ICorDebugHeapEnum
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794432"
---
# <a name="icordebugheapenum-interface"></a>Interface ICorDebugHeapEnum
Fornece um enumerador para objetos no heap gerenciado. Essa interface é uma subclasse da interface ICorDebugEnum.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](icordebugheapenum-next-method.md)|Obtém o número especificado de instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) que contêm informações sobre objetos no heap gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugHeapEnum` implementa a interface ICorDebugEnum.  
  
 Uma instância de `ICorDebugHeapEnum` é populada com instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) chamando o método [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) . Cada instância de [COR_HEAPOBJECT](cor-heapobject-structure.md) na coleção representa um objeto dinâmico no heap ou um objeto que não tem raiz por nenhum objeto, mas ainda não foi coletado pelo coletor de lixo. Os objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) na coleção podem ser enumerados chamando o método [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
