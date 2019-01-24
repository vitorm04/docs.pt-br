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
ms.openlocfilehash: e26a90b6725d53774053293c04842b761da6ab12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717669"
---
# <a name="identityattribute-structure"></a>Estrutura IDENTITY_ATTRIBUTE
Contém informações de atributo de metadados sobre um [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instância.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
