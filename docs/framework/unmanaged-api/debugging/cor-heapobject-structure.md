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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c59ddec655f3127e8dab8d8c41543f03a896cf63
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274031"
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
 `COR_HEAPOBJECT`as instâncias podem ser recuperadas enumerando um objeto de interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) que é populado chamando o método [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) .  
  
 Uma `COR_HEAPOBJECT` instância do fornece informações sobre um objeto ao vivo no heap gerenciado ou sobre um objeto que não tem raiz por nenhum objeto, mas que ainda não foi coletado pelo coletor de lixo.  
  
 Para obter um melhor desempenho `COR_HEAPOBJECT.address` , o campo `CORDB_ADDRESS` é um valor em vez do valor da interface ICorDebugValue usado em grande parte da API de depuração. Para obter um objeto ICorDebugValue para um determinado endereço de objeto, você pode passar `CORDB_ADDRESS` o valor para o método [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .  
  
 Para obter um melhor desempenho `COR_HEAPOBJECT.type` , o campo `COR_TYPEID` é um valor em vez do valor da interface ICorDebugType usado em grande parte da API de depuração. Para obter um objeto ICorDebugType para uma determinada ID de tipo, você pode passar `COR_TYPEID` o valor para o método [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) .  
  
 A `COR_HEAPOBJECT` estrutura inclui uma interface com contada com referência. Se você recuperar uma `COR_HEAPOBJECT` instância do enumerador chamando o método [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) , você deverá liberar a referência posteriormente.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
