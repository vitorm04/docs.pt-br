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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c0b45e08f7b88d9374023f95c6e3e22139c8949
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144762"
---
# <a name="icordebugvalue3getsize64-method"></a>Método ICorDebugValue3::GetSize64
Obtém o tamanho, em bytes, isso [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pSize  
 [out] Um ponteiro para o tamanho, em bytes, do objeto.  
  
## <a name="remarks"></a>Comentários  
 Se o tipo de valor, esse é um tipo de referência, esse método retorna o tamanho do ponteiro em vez do tamanho do objeto.  
  
 O `ICorDebugValue3::GetSize` difere do método de [icordebugvalue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) método no tipo de seu parâmetro de saída. Na [icordebugvalue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), o parâmetro de saída é um `ULONG32`; na `ICorDebugValue3::GetSize`, é um `ULONG64`. Isso permite que o [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface para relatar o tamanho das matrizes que exceda 2 GB.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
