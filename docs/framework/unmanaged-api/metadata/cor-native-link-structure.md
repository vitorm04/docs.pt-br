---
title: Estrutura COR_NATIVE_LINK
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177953"
---
# <a name="cor_native_link-structure"></a>Estrutura COR_NATIVE_LINK
Contém informações usadas para vincular código nativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`m_linkType`|O tipo a ser ligado em código nativo. Esse valor é um dos valores [cornativeLinkType.](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)|  
|`m_flags`|Sinalizadores usados pelo linker ao vincular código nativo. Esse valor é um dos valores [do CorNativeLinkFlags.](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)|  
|`m_entryPoint`|O token de metadados MemberRef que representa o ponto de entrada. O formato é `lib:entrypoint`.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Estruturas de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [Enumeração CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [Enumeração CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
