---
title: Método IMetaDataAssemblyEmit::SetExportedTypeProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8643a4d207fb570195caa00a1ac659c78c2ff2b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a>Método IMetaDataAssemblyEmit::SetExportedTypeProps
Modifica especificado `ExportedType` estrutura de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ct`  
 [in] O token de metadados que especifica o `ExportedType` estrutura de metadados a ser modificado.  
  
 `tkImplementation`  
 [in] O token, do tipo `File`, `AssemblyRef`, ou `ExportedType`, que especifica como este tipo é implementado.  
  
 `tkTypeDef`  
 [in] O `TypeDef` referenciado no arquivo de código de token.  
  
 `dwExportedTypeFlags`  
 [in] Uma combinação bit a bit de valores que especificam os atributos do tipo.  
  
## <a name="remarks"></a>Comentários  
 Para criar um `ExportedType` estrutura de metadados, use o [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
