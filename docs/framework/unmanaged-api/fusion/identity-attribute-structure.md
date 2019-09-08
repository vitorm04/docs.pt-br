---
title: Estrutura IDENTITY_ATTRIBUTE
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796488"
---
# <a name="identity_attribute-structure"></a>Estrutura IDENTITY_ATTRIBUTE
Contém informações de atributo de metadados sobre uma instância de [IDefinitionIdentity](idefinitionidentity-interface.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`pszNamespace`|Um ponteiro para uma cadeia de caracteres de caractere terminada em nulo que contém o namespace no qual o atributo está.|  
|`pszName`|Um ponteiro para uma cadeia de caracteres de caractere terminada em nulo que contém o nome do atributo.|  
|`pszValue`|Um ponteiro para uma cadeia de caracteres de caractere terminada em nulo que contém o valor do atributo.|  
  
## <a name="remarks"></a>Comentários  
 A `IDENTITY_ATTRIBUTE` estrutura contém três ponteiros para cadeias de caracteres terminadas em nulo. Essas três cadeias de caracteres descrevem um atributo.  
  
 Uma instância de uma `IDENTITY_ATTRIBUTE` estrutura é associada a uma instância de uma estrutura [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) . A `IDENTITY_ATTRIBUTE` estrutura contém as cadeias de caracteres reais e `IDENTITY_ATTRIBUTE_BLOB` a estrutura correspondente lista os deslocamentos para as `IDENTITY_ATTRIBUTE` três cadeias de caracteres listadas na estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolamento. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IDefinitionIdentity](idefinitionidentity-interface.md)
- [Estrutura IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md)
- [Estruturas de fusão](fusion-structures.md)
