---
title: Estrutura COR_TYPE_LAYOUT
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd274b1eb14532629580e777288317186544912
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274159"
---
# <a name="cor_type_layout-structure"></a>Estrutura COR_TYPE_LAYOUT
Fornece informações sobre o layout de um objeto na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`parentID`|O identificador do tipo pai para esse tipo. Essa será a ID de tipo nulo (token1 = 0, token2 = 0) se a ID de tipo corresponder <xref:System.Object?displayProperty=nameWithType>a.|  
|`objectSize`|O tamanho de base de um objeto deste tipo. Este é o tamanho total para objetos que não são de tamanho variável.|  
|`numFields`|O número de campos incluídos em objetos deste tipo.|  
|`boxOffset`|Se esse tipo for in box, o deslocamento inicial dos campos de um objeto. Esse campo é válido somente para tipos de valor como primitivos e estruturas.|  
|`type`|O CorElementType ao qual esse tipo pertence.|  
  
## <a name="remarks"></a>Comentários  
 Se `numFields` for maior que zero, você poderá chamar o método [ICorDebugProcess5:: GetTypeFields](icordebugprocess5-gettypefields-method.md) para obter informações sobre os campos nesse tipo. Se `type` for `ELEMENT_TYPE_STRING` ,`ELEMENT_TYPE_ARRAY`, ou`ELEMENT_TYPE_SZARRAY`, o tamanho dos objetos desse tipo é variável e você pode passar a estrutura [COR_TYPEID](cor-typeid-structure.md) para o método [ICorDebugProcess5:: GetArrayLayout](icordebugprocess5-getarraylayout-method.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
