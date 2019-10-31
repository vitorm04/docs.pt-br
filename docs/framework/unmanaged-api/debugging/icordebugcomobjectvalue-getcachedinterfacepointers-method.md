---
title: Método ICorDebugComObjectValue::GetCachedInterfacePointers
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: c1e2b557a5e5794c50986b1af8ec39faba845cc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125509"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>Método ICorDebugComObjectValue::GetCachedInterfacePointers
Obtém os ponteiros de interface bruto armazenados em cache no RCW (tempo de execução Callable Wrapper) atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bIInspectableOnly`  
 no Um valor que indica se o método retornará apenas interfaces Windows Runtime (interfaces`IInspectable`) ou todas as interfaces COM armazenadas em cache pelo RCW (Runtime Callable Wrapper).  
  
 `celt`  
 no O número de objetos cujos endereços devem ser recuperados.  
  
 `pceltFetched`  
 fora Um ponteiro para o número de `CORDB_ADDRESS` valores realmente retornados em `ptrs`.  
  
 `ptrs`  
 Um ponteiro para o endereço inicial de uma matriz de `CORDB_ADDRESS` valores que contêm os endereços dos objetos de interface em cache.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugComObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
