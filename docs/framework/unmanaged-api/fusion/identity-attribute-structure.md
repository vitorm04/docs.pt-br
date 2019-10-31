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
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107977"
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
 A estrutura de `IDENTITY_ATTRIBUTE` contém três ponteiros para cadeias de caracteres terminadas em nulo. Essas três cadeias de caracteres descrevem um atributo.  
  
 Uma instância de uma estrutura de `IDENTITY_ATTRIBUTE` é associada a uma instância de uma estrutura [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) . A estrutura de `IDENTITY_ATTRIBUTE` contém as cadeias de caracteres reais e a estrutura de `IDENTITY_ATTRIBUTE_BLOB` correspondente lista os deslocamentos para as três cadeias de caracteres listadas na estrutura de `IDENTITY_ATTRIBUTE`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolamento. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IDefinitionIdentity](idefinitionidentity-interface.md)
- [Estrutura IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md)
- [Estruturas de fusão](fusion-structures.md)
