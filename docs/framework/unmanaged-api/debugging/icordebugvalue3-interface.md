---
title: Interface ICorDebugValue3
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 5fa042223e47961dad0a6799ab8ca999ef76e285
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791088"
---
# <a name="icordebugvalue3-interface"></a>Interface ICorDebugValue3
Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para fornecer suporte a matrizes com mais de 2 GB.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetSize64](icordebugvalue3-getsize64-method.md)|Obtém o tamanho, em bytes, deste `ICorDebugValue3` objeto.|  
  
## <a name="remarks"></a>Comentários  
 O método [ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) retorna um tamanho de objeto que varia de 0 a 2.147.483.647 bytes. No .NET Framework 4,5, o tamanho das matrizes pode exceder 2 GB. A interface `ICorDebugValue3` permite que você determine o tamanho dessas matrizes.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
