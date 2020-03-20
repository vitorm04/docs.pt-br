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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179329"
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
 `COR_HEAPOBJECT`as instâncias podem ser recuperadas enumerando um objeto de interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) que é preenchido chamando o método [ICorDebugProcess5::EnumerateHeap.](icordebugprocess5-enumerateheap-method.md)  
  
 Uma `COR_HEAPOBJECT` instância fornece informações sobre um objeto vivo no heap gerenciado ou sobre um objeto que não está enraizado em nenhum objeto, mas ainda não foi coletado pelo coletor de lixo.  
  
 Para um melhor `COR_HEAPOBJECT.address` desempenho, `CORDB_ADDRESS` o campo é um valor em vez do valor de interface ICorDebugValue usado em grande parte da API de depuração. Para obter um objeto ICorDebugValue para um determinado `CORDB_ADDRESS` endereço de objeto, você pode passar o valor para o método [ICorDebugProcess5::GetObject.](icordebugprocess5-getobject-method.md)  
  
 Para um melhor `COR_HEAPOBJECT.type` desempenho, `COR_TYPEID` o campo é um valor em vez do valor de interface ICorDebugType usado em grande parte da API de depuração. Para obter um objeto ICorDebugType para um determinado `COR_TYPEID` tipo DeI, você pode passar o valor para o método [ICorDebugProcess5::GetTypeForTypeID.](icordebugprocess5-gettypefortypeid-method.md)  
  
 A `COR_HEAPOBJECT` estrutura inclui uma interface COM contada com referência. Se você `COR_HEAPOBJECT` recuperar uma instância do enumerador chamando o [método ICorDebugHeapEnum::Next,](icordebugheapenum-next-method.md) você deve posteriormente liberar a referência.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
