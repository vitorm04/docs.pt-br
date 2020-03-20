---
title: Método ICorDebugHeapEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: f5af8e559b4fbfeb60530372185ca10104ade987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178858"
---
# <a name="icordebugheapenumnext-method"></a>Método ICorDebugHeapEnum::Next
Obtém o número especificado de [COR_HEAPOBJECT](cor-heapobject-structure.md) instâncias que contêm informações sobre objetos no heap gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 Celt  
 [em] O número de objetos a serem recuperados.  
  
 objetos  
 [fora] Uma matriz de ponteiros, cada um dos quais aponta para um [objeto COR_HEAPOBJECT](cor-heapobject-structure.md) que fornece informações sobre um objeto no heap gerenciado.  
  
 pceltFetched  
 [fora] Um ponteiro para o número de `objects` [objetos COR_HEAPOBJECT](cor-heapobject-structure.md) realmente retornado em . Este valor `null` pode `celt` ser se for 1.  
  
## <a name="remarks"></a>Comentários  
 O `COR_HEAPOBJECT.type` campo é o identificador de uma interface COM contada com referência sinuosa. Esta referência deve ser liberada `ICorDebugHeapEnum::Next`pelo chamador de .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugHeapEnum](icordebugheapenum-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
