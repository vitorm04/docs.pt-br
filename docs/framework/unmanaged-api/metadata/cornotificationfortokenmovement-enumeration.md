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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a7859bd890a2ecc10b5117f697ff8b06ad569f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781696"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>Enumeração CorNotificationForTokenMovement
Especifica as notificações que serão enviadas para o cliente da API de metadados quando ocorre um remapeamento do token.  
  
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
  
|Membro|Descrição|  
|------------|-----------------|  
|`MDNotifyDefault`|Notificar quando `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, ou `mdFieldDef` movimentação de tokens.|  
|`MDNotifyAll`|Notificar quando qualquer token move.|  
|`MDNotifyNone`|Notifica quando mover de tokens.|  
|`MDNotifyMethodDef`|Notificar quando um `mdMethodDef` movimentações de token.|  
|`MDNotifyMemberRef`|Notificar quando um `mdMemberRef` movimentações de token.|  
|`MDNotifyFieldDef`|Notificar quando um `mdFieldDef` movimentações de token.|  
|`MDNotifyTypeRef`|Notificar quando um `mdTypeRef` movimentações de token.|  
|`MDNotifyTypeDef`|Notificar quando um `mdTypeDef` movimentações de token.|  
|`MDNotifyParamDef`|Notificar quando um `mdParamDef` movimentações de token.|  
|`MDNotifyInterfaceImpl`|Notificar quando um `mdInterfaceImpl` movimentações de token.|  
|`MDNotifyProperty`|Notificar quando um `mdProperty` movimentações de token.|  
|`MDNotifyEvent`|Notificar quando um `mdEvent` movimentações de token.|  
|`MDNotifySignature`|Notificar quando um `mdSignature` movimentações de token.|  
|`MDNotifyTypeSpec`|Notificar quando um `mdTypeSpec` movimentações de token.|  
|`MDNotifyCustomAttribute`|Notificar quando um `mdCustomAttribute` movimentações de token.|  
|`MDNotifySecurityValue`|Notificar quando um `mdSecurityValue` movimentações de token.|  
|`MDNotifyPermission`|Notificar quando um `mdPermission` movimentações de token.|  
|`MDNotifyModuleRef`|Notificar quando um `mdModuleRef` movimentações de token.|  
|`MDNotifyNameSpace`|Notificar quando um `mdNameSpace` movimentações de token.|  
|`MDNotifyAssemblyRef`|Notificar quando um `mdAssemblyRef` movimentações de token.|  
|`MDNotifyFile`|Notificar quando um `mdFile` movimentações de token.|  
|`MDNotifyExportedType`|Notificar quando um `mdExportedType` movimentações de token.|  
|`MDNotifyResource`|Notificar quando um `mdManifestResource` movimentações de token.|  
  
## <a name="remarks"></a>Comentários  
 Um token pode ser novamente mapeado (que é, movido) durante uma mesclagem de metadados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
