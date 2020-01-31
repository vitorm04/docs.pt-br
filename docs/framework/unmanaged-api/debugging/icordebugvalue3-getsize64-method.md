---
title: Método ICorDebugValue3::GetSize64
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: 7ae06d825565faff70b0c8be2ccbee5228737e41
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791099"
---
# <a name="icordebugvalue3getsize64-method"></a>Método ICorDebugValue3::GetSize64
Obtém o tamanho, em bytes, deste objeto [ICorDebugValue3](icordebugvalue3-interface.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pSize  
 fora Um ponteiro para o tamanho, em bytes, deste objeto.  
  
## <a name="remarks"></a>Comentários  
 Se o tipo desse valor for um tipo de referência, esse método retornará o tamanho do ponteiro em vez do tamanho do objeto.  
  
 O método `ICorDebugValue3::GetSize` difere do método [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) no tipo de seu parâmetro de saída. Em [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md), o parâmetro de saída é um `ULONG32`; em `ICorDebugValue3::GetSize`, é um `ULONG64`. Isso permite que a interface [ICorDebugValue3](icordebugvalue3-interface.md) relate o tamanho das matrizes que excedem 2GB.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugValue3](icordebugvalue3-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
