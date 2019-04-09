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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074866"
---
# <a name="corcheckduplicatesfor-enumeration"></a>Enumeração CorCheckDuplicatesFor
Especifica os tokens de metadados que serão verificados duplicatas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`MDDupAll`|Verifique se todos os tokens de metadados para as duplicatas.|  
|`MDDupENC`|Não usado.|  
|`MDNoDupChecks`|Não verificam os tokens de metadados para as duplicatas.|  
|`MDDupTypeDef`|Verificar se há duplicatas de `mdTypeDef` tokens.|  
|`MDDupInterfaceImpl`|Verificar se há duplicatas de `mdInterfaceImpl` tokens.|  
|`MDDupMethodDef`|Verificar se há duplicatas de `mdMethodDef` tokens.|  
|`MDDupTypeRef`|Verificar se há duplicatas de `mdTypeRef` tokens.|  
|`MDDupMemberRef`|Verificar se há duplicatas de `mdMemberRef` tokens.|  
|`MDDupCustomAttribute`|Verificar se há duplicatas de `mdCustomAttribute` tokens.|  
|`MDDupParamDef`|Verificar se há duplicatas de `mdParamDef` tokens.|  
|`MDDupPermission`|Verificar se há duplicatas de `mdPermission` tokens.|  
|`MDDupProperty`|Verificar se há duplicatas de `mdProperty` tokens.|  
|`MDDupEvent`|Verificar se há duplicatas de `mdEvent` tokens.|  
|`MDDupFieldDef`|Verificar se há duplicatas de `mdFieldDef` tokens.|  
|`MDDupSignature`|Verificar se há duplicatas de `mdSignature` tokens.|  
|`MDDupModuleRef`|Verificar se há duplicatas de `mdModuleRef` tokens.|  
|`MDDupTypeSpec`|Verificar se há duplicatas de `mdTypeSpec` tokens.|  
|`MDDupImplMap`|Verificar se há duplicatas de `mdImplMap` tokens.|  
|`MDDupAssemblyRef`|Verificar se há duplicatas de `mdAssemblyRef` tokens.|  
|`MDDupFile`|Verificar se há duplicatas de `mdFile` tokens.|  
|`MDDupExportedType`|Verificar se há duplicatas de `mdExportedType` tokens.|  
|`MDDupManifestResource`|Verificar se há duplicatas de `mdManifestResource` tokens.|  
|`MDDupGenericParam`|Verificar se há duplicatas de `mdGenericParam` tokens.|  
|`MDDupMethodSpec`|Verificar se há duplicatas de `mdMethodSpec` tokens.|  
|`MDDupGenericParamConstraint`|Verificar se há duplicatas de `mdGenericParamConstraint` tokens.|  
|`MDDupAssembly`|Verificar se há duplicatas de `mdAssembly` tokens.|  
|`MDDupDefault`|Verificar se há duplicatas `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, e `mdMethodSpec` tokens.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
