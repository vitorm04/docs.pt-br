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
ms.openlocfilehash: 7efb2c3e8033b8bd8fa736a29b2ab9b3bedebeaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609497"
---
# <a name="cortypelayout-structure"></a>Estrutura COR_TYPE_LAYOUT
Fornece informações sobre o layout de um objeto na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`parentID`|O identificador do tipo pai para esse tipo. Esta será a id de tipo nulo (token1 = 0, token2 = 0) se a id de tipo corresponde ao <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|O tamanho da base de um objeto desse tipo. Esse é o tamanho total de objetos de tamanho não variável.|  
|`numFields`|O número de campos incluídos em objetos desse tipo.|  
|`boxOffset`|Se esse tipo é demarcado, o início de deslocamento de campos de um objeto. Este campo é válido somente para tipos de valor, como primitivos e estruturas.|  
|`type`|O CorElementType ao qual pertence esse tipo.|  
  
## <a name="remarks"></a>Comentários  
 Se `numFields` é maior que zero, você pode chamar o [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) método para obter informações sobre os campos nesse tipo. Se `type` está `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, ou `ELEMENT_TYPE_SZARRAY`, o tamanho dos objetos desse tipo é variável, e você pode passar o [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) estrutura para o [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
