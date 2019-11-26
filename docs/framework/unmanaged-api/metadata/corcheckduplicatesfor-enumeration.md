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
ms.openlocfilehash: 6b551743227dc1c6069796038782a515e6dbe8c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443782"
---
# <a name="corcheckduplicatesfor-enumeration"></a>Enumeração CorCheckDuplicatesFor
Especifica os tokens de metadados que serão verificados em busca de duplicatas.  
  
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
|`MDDupAll`|Verifique se há duplicatas em todos os tokens de metadados.|  
|`MDDupENC`|Não usado.|  
|`MDNoDupChecks`|Não verifique os tokens de metadados em busca de duplicatas.|  
|`MDDupTypeDef`|Verifique se há duplicatas de tokens de `mdTypeDef`.|  
|`MDDupInterfaceImpl`|Verifique se há duplicatas de tokens de `mdInterfaceImpl`.|  
|`MDDupMethodDef`|Verifique se há duplicatas de tokens de `mdMethodDef`.|  
|`MDDupTypeRef`|Verifique se há duplicatas de tokens de `mdTypeRef`.|  
|`MDDupMemberRef`|Verifique se há duplicatas de tokens de `mdMemberRef`.|  
|`MDDupCustomAttribute`|Verifique se há duplicatas de tokens de `mdCustomAttribute`.|  
|`MDDupParamDef`|Verifique se há duplicatas de tokens de `mdParamDef`.|  
|`MDDupPermission`|Verifique se há duplicatas de tokens de `mdPermission`.|  
|`MDDupProperty`|Verifique se há duplicatas de tokens de `mdProperty`.|  
|`MDDupEvent`|Verifique se há duplicatas de tokens de `mdEvent`.|  
|`MDDupFieldDef`|Verifique se há duplicatas de tokens de `mdFieldDef`.|  
|`MDDupSignature`|Verifique se há duplicatas de tokens de `mdSignature`.|  
|`MDDupModuleRef`|Verifique se há duplicatas de tokens de `mdModuleRef`.|  
|`MDDupTypeSpec`|Verifique se há duplicatas de tokens de `mdTypeSpec`.|  
|`MDDupImplMap`|Verifique se há duplicatas de tokens de `mdImplMap`.|  
|`MDDupAssemblyRef`|Verifique se há duplicatas de tokens de `mdAssemblyRef`.|  
|`MDDupFile`|Verifique se há duplicatas de tokens de `mdFile`.|  
|`MDDupExportedType`|Verifique se há duplicatas de tokens de `mdExportedType`.|  
|`MDDupManifestResource`|Verifique se há duplicatas de tokens de `mdManifestResource`.|  
|`MDDupGenericParam`|Verifique se há duplicatas de tokens de `mdGenericParam`.|  
|`MDDupMethodSpec`|Verifique se há duplicatas de tokens de `mdMethodSpec`.|  
|`MDDupGenericParamConstraint`|Verifique se há duplicatas de tokens de `mdGenericParamConstraint`.|  
|`MDDupAssembly`|Verifique se há duplicatas de tokens de `mdAssembly`.|  
|`MDDupDefault`|Verifique se há duplicatas de `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`e tokens de `mdMethodSpec`.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
