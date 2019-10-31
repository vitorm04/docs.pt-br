---
title: Estrutura COR_HEAPOBJECT
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099074"
---
# <a name="cor_heapobject-structure"></a>Estrutura COR_HEAPOBJECT
Fornece informações sobre um objeto no heap gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`address`|O endereço do objeto na memória.|  
|`size`|O tamanho total do objeto, em bytes.|  
|`type`|Um token [COR_TYPEID](cor-typeid-structure.md) que representa o tipo do objeto.|  
  
## <a name="remarks"></a>Comentários  
 `COR_HEAPOBJECT` instâncias podem ser recuperadas enumerando um objeto de interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) que é populado chamando o método [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) .  
  
 Uma instância de `COR_HEAPOBJECT` fornece informações sobre um objeto ao vivo no heap gerenciado ou sobre um objeto que não é enraizada por nenhum objeto, mas que ainda não foi coletado pelo coletor de lixo.  
  
 Para obter um melhor desempenho, o campo `COR_HEAPOBJECT.address` é um valor de `CORDB_ADDRESS`, e não o valor da interface ICorDebugValue usado em grande parte da API de depuração. Para obter um objeto ICorDebugValue para um determinado endereço de objeto, você pode passar o valor `CORDB_ADDRESS` para o método [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .  
  
 Para obter um melhor desempenho, o campo `COR_HEAPOBJECT.type` é um valor de `COR_TYPEID`, e não o valor da interface ICorDebugType usado em grande parte da API de depuração. Para obter um objeto ICorDebugType para uma determinada ID de tipo, você pode passar o valor `COR_TYPEID` para o método [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) .  
  
 A estrutura de `COR_HEAPOBJECT` inclui uma interface COM contada COM referência. Se você recuperar uma instância de `COR_HEAPOBJECT` do enumerador chamando o método [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) , você deverá liberar a referência posteriormente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
