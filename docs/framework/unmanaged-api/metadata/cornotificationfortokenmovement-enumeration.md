---
title: Enumeração CorNotificationForTokenMovement
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450151"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>Enumeração CorNotificationForTokenMovement
Especifica as notificações que serão enviadas para o cliente da API de metadados quando ocorrer um remapeamento de token.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`MDNotifyDefault`|Notificar quando os tokens `mdTypeRef`, `mdMethodDef`, `mdMemberRef`ou `mdFieldDef` forem movidos.|  
|`MDNotifyAll`|Notificar quando qualquer token for movido.|  
|`MDNotifyNone`|Não notificar quando os tokens forem movidos.|  
|`MDNotifyMethodDef`|Notificar quando um token de `mdMethodDef` se mover.|  
|`MDNotifyMemberRef`|Notificar quando um token de `mdMemberRef` se mover.|  
|`MDNotifyFieldDef`|Notificar quando um token de `mdFieldDef` se mover.|  
|`MDNotifyTypeRef`|Notificar quando um token de `mdTypeRef` se mover.|  
|`MDNotifyTypeDef`|Notificar quando um token de `mdTypeDef` se mover.|  
|`MDNotifyParamDef`|Notificar quando um token de `mdParamDef` se mover.|  
|`MDNotifyInterfaceImpl`|Notificar quando um token de `mdInterfaceImpl` se mover.|  
|`MDNotifyProperty`|Notificar quando um token de `mdProperty` se mover.|  
|`MDNotifyEvent`|Notificar quando um token de `mdEvent` se mover.|  
|`MDNotifySignature`|Notificar quando um token de `mdSignature` se mover.|  
|`MDNotifyTypeSpec`|Notificar quando um token de `mdTypeSpec` se mover.|  
|`MDNotifyCustomAttribute`|Notificar quando um token de `mdCustomAttribute` se mover.|  
|`MDNotifySecurityValue`|Notificar quando um token de `mdSecurityValue` se mover.|  
|`MDNotifyPermission`|Notificar quando um token de `mdPermission` se mover.|  
|`MDNotifyModuleRef`|Notificar quando um token de `mdModuleRef` se mover.|  
|`MDNotifyNameSpace`|Notificar quando um token de `mdNameSpace` se mover.|  
|`MDNotifyAssemblyRef`|Notificar quando um token de `mdAssemblyRef` se mover.|  
|`MDNotifyFile`|Notificar quando um token de `mdFile` se mover.|  
|`MDNotifyExportedType`|Notificar quando um token de `mdExportedType` se mover.|  
|`MDNotifyResource`|Notificar quando um token de `mdManifestResource` se mover.|  
  
## <a name="remarks"></a>Comentários  
 Um token pode ser mapeado novamente (ou seja, movido) durante uma mesclagem de metadados.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
