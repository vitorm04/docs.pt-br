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
ms.openlocfilehash: 2c84112984e9cb7dec2a492ac16af00e14770806
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782490"
---
# <a name="icordebugheapenumnext-method"></a>Método ICorDebugHeapEnum::Next
Obtém o número especificado de instâncias de [COR_HEAPOBJECT](cor-heapobject-structure.md) que contêm informações sobre objetos no heap gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 celt  
 no O número de objetos a serem recuperados.  
  
 objetos  
 fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [COR_HEAPOBJECT](cor-heapobject-structure.md) que fornece informações sobre um objeto no heap gerenciado.  
  
 pceltFetched  
 fora Um ponteiro para o número de objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) realmente retornados em `objects`. Esse valor pode ser `null` se `celt` for 1.  
  
## <a name="remarks"></a>Comentários  
 O campo `COR_HEAPOBJECT.type` é o identificador de uma interface COM contada COM referência aninhada. Essa referência deve ser liberada pelo chamador de `ICorDebugHeapEnum::Next`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugHeapEnum](icordebugheapenum-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
