---
title: Enumeração CorTokenType
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 74807a678b5c0c2738f33fe552f6462af93ca1f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436457"
---
# <a name="cortokentype-enumeration"></a>Enumeração CorTokenType
Indica o tipo de um token de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`mdtModule`|Um token `mdModule`.|  
|`mdtTypeRef`|Um token `mdTypeRef`.|  
|`mdtTypeDef`|Um token `mdTypeDef`.|  
|`mdtFieldDef`|Um token `mdFieldDef`.|  
|`mdtMethodDef`|Um token `mdMethodDef`.|  
|`mdtParamDef`|Um token `mdParamDef`.|  
|`mdtInterfaceImpl`|Um token `mdInterfaceImpl`.|  
|`mdtMemberRef`|Um token `mdMemberRef`.|  
|`mdtCustomAttribute`|Um token `mdCustomAttribute`.|  
|`mdtPermission`|Um token `mdPermission`.|  
|`mdtSignature`|Um token `mdSignature`.|  
|`mdtEvent`|Um token `mdEvent`.|  
|`mdtProperty`|Um token `mdProperty`.|  
|`mdtModuleRef`|Um token `mdModuleRef`.|  
|`mdtTypeSpec`|Um token `mdTypeSpec`.|  
|`mdtAssembly`|Um token `mdAssembly`.|  
|`mdtAssemblyRef`|Um token `mdAssemblyRef`.|  
|`mdtFile`|Um token `mdFile`.|  
|`mdtExportedType`|Um token `mdExportedType`.|  
|`mdtManifestResource`|Um token `mdManifestResource`.|  
|`mdtGenericParam`|Um token `mdGenericParam`.|  
|`mdtMethodSpec`|Um token `mdMethodSpec`.|  
|`mdtGenericParamConstraint`|Um token `mdGenericParamConstraint`.|  
|`mdtString`|Um token `mdString`.|  
|`mdtName`|Um token `mdName`.|  
|`mdtBaseType`|Não usado.|  
  
## <a name="remarks"></a>Comentários  
 Cada valor é igual ao valor do byte superior no token de metadados correspondente.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
