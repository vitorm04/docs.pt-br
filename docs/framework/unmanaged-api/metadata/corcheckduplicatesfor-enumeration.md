---
title: Enumeração CorCheckDuplicatesFor
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176182"
---
# <a name="corcheckduplicatesfor-enumeration"></a>Enumeração CorCheckDuplicatesFor
Especifica os tokens de metadados que serão verificados para duplicatas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`MDDupAll`|Verifique todos os tokens de metadados para duplicatas.|  
|`MDDupENC`|Não usado.|  
|`MDNoDupChecks`|Não verifique os tokens de metadados para duplicatas.|  
|`MDDupTypeDef`|Verifique se há `mdTypeDef` duplicatas de tokens.|  
|`MDDupInterfaceImpl`|Verifique se há `mdInterfaceImpl` duplicatas de tokens.|  
|`MDDupMethodDef`|Verifique se há `mdMethodDef` duplicatas de tokens.|  
|`MDDupTypeRef`|Verifique se há `mdTypeRef` duplicatas de tokens.|  
|`MDDupMemberRef`|Verifique se há `mdMemberRef` duplicatas de tokens.|  
|`MDDupCustomAttribute`|Verifique se há `mdCustomAttribute` duplicatas de tokens.|  
|`MDDupParamDef`|Verifique se há `mdParamDef` duplicatas de tokens.|  
|`MDDupPermission`|Verifique se há `mdPermission` duplicatas de tokens.|  
|`MDDupProperty`|Verifique se há `mdProperty` duplicatas de tokens.|  
|`MDDupEvent`|Verifique se há `mdEvent` duplicatas de tokens.|  
|`MDDupFieldDef`|Verifique se há `mdFieldDef` duplicatas de tokens.|  
|`MDDupSignature`|Verifique se há `mdSignature` duplicatas de tokens.|  
|`MDDupModuleRef`|Verifique se há `mdModuleRef` duplicatas de tokens.|  
|`MDDupTypeSpec`|Verifique se há `mdTypeSpec` duplicatas de tokens.|  
|`MDDupImplMap`|Verifique se há `mdImplMap` duplicatas de tokens.|  
|`MDDupAssemblyRef`|Verifique se há `mdAssemblyRef` duplicatas de tokens.|  
|`MDDupFile`|Verifique se há `mdFile` duplicatas de tokens.|  
|`MDDupExportedType`|Verifique se há `mdExportedType` duplicatas de tokens.|  
|`MDDupManifestResource`|Verifique se há `mdManifestResource` duplicatas de tokens.|  
|`MDDupGenericParam`|Verifique se há `mdGenericParam` duplicatas de tokens.|  
|`MDDupMethodSpec`|Verifique se há `mdMethodSpec` duplicatas de tokens.|  
|`MDDupGenericParamConstraint`|Verifique se há `mdGenericParamConstraint` duplicatas de tokens.|  
|`MDDupAssembly`|Verifique se há `mdAssembly` duplicatas de tokens.|  
|`MDDupDefault`|Verifique se há `mdMemberRef` `mdTypeRef`duplicatas de , `mdSignature`, e `mdTypeSpec` `mdMethodSpec` tokens.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
