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
ms.openlocfilehash: de1646cdbc11369b43a821d8b762879d1df7ed2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751539"
---
# <a name="identityattribute-structure"></a>Estrutura IDENTITY_ATTRIBUTE
Contém informações de atributo de metadados sobre um [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instância.  
  
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
|`pszNamespace`|Um ponteiro para uma cadeia de caracteres terminada em nulo que contém o namespace que o atributo está em.|  
|`pszName`|Um ponteiro para uma cadeia de caracteres terminada em nulo que contém o nome do atributo.|  
|`pszValue`|Um ponteiro para uma cadeia de caracteres terminada em nulo que contém o valor do atributo.|  
  
## <a name="remarks"></a>Comentários  
 O `IDENTITY_ATTRIBUTE` estrutura contém três ponteiros para cadeias de caracteres terminada em nulo. Essas três cadeias de caracteres descrevem um atributo.  
  
 Uma instância de um `IDENTITY_ATTRIBUTE` estrutura está associada uma instância de um [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) estrutura. O `IDENTITY_ATTRIBUTE` estrutura contém as cadeias de caracteres reais e correspondente `IDENTITY_ATTRIBUTE_BLOB` estrutura lista os deslocamentos de três cadeias de caracteres listadas no `IDENTITY_ATTRIBUTE` estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [Estrutura IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [Estruturas de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
