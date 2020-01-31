---
title: Interface ICorDebugValueEnum
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
ms.openlocfilehash: ba61df045caa117acae3756eb879cf67d0791222
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791059"
---
# <a name="icordebugvalueenum-interface"></a>Interface ICorDebugValueEnum
Implementa os métodos "ICorDebugEnum" e enumera as matrizes "ICorDebugValue".  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](icordebugvalueenum-next-method.md)|Obtém o número especificado de instâncias de `ICorDebugValue` da enumeração, começando na posição atual.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
