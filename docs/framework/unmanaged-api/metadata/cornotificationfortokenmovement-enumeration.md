---
title: "Enumeração CorNotificationForTokenMovement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNotificationForTokenMovement
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNotificationForTokenMovement
helpviewer_keywords: CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e1d3ad11867dbd06dfe3f43cc31817a44cb96d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cornotificationfortokenmovement-enumeration"></a>Enumeração CorNotificationForTokenMovement
Especifica as notificações serão enviadas para o cliente de API de metadados quando um token remapeamento ocorre.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`MDNotifyNone`|Não notifica quando mover tokens.|  
|`MDNotifyMethodDef`|Notificar quando um `mdMethodDef` move de token.|  
|`MDNotifyMemberRef`|Notificar quando um `mdMemberRef` move de token.|  
|`MDNotifyFieldDef`|Notificar quando um `mdFieldDef` move de token.|  
|`MDNotifyTypeRef`|Notificar quando um `mdTypeRef` move de token.|  
|`MDNotifyTypeDef`|Notificar quando um `mdTypeDef` move de token.|  
|`MDNotifyParamDef`|Notificar quando um `mdParamDef` move de token.|  
|`MDNotifyInterfaceImpl`|Notificar quando um `mdInterfaceImpl` move de token.|  
|`MDNotifyProperty`|Notificar quando um `mdProperty` move de token.|  
|`MDNotifyEvent`|Notificar quando um `mdEvent` move de token.|  
|`MDNotifySignature`|Notificar quando um `mdSignature` move de token.|  
|`MDNotifyTypeSpec`|Notificar quando um `mdTypeSpec` move de token.|  
|`MDNotifyCustomAttribute`|Notificar quando um `mdCustomAttribute` move de token.|  
|`MDNotifySecurityValue`|Notificar quando um `mdSecurityValue` move de token.|  
|`MDNotifyPermission`|Notificar quando um `mdPermission` move de token.|  
|`MDNotifyModuleRef`|Notificar quando um `mdModuleRef` move de token.|  
|`MDNotifyNameSpace`|Notificar quando um `mdNameSpace` move de token.|  
|`MDNotifyAssemblyRef`|Notificar quando um `mdAssemblyRef` move de token.|  
|`MDNotifyFile`|Notificar quando um `mdFile` move de token.|  
|`MDNotifyExportedType`|Notificar quando um `mdExportedType` move de token.|  
|`MDNotifyResource`|Notificar quando um `mdManifestResource` move de token.|  
  
## <a name="remarks"></a>Comentários  
 Um token pode ser novamente mapeado (que é, movidos) durante a mesclagem de metadados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
