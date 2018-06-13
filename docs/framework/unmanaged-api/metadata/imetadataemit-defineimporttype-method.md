---
title: Método IMetaDataEmit::DefineImportType
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68e6f7599db55ed9429f159b380a8a9f8ae3f034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447480"
---
# <a name="imetadataemitdefineimporttype-method"></a>Método IMetaDataEmit::DefineImportType
Cria uma referência para o tipo especificado que está definido fora do escopo atual e define um token para essa referência.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAssemImport`  
 [in] Um [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface que representa o assembly do qual o tipo de destino é importado.  
  
 `pbHashValue`  
 [in] Uma matriz que contém o hash para o conjunto especificado por `pAssemImport`.  
  
 `cbHashValue`  
 [in] O número de bytes a `pbHashValue` matriz.  
  
 `pImport`  
 [in] Um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface que representa o escopo de metadados do qual o tipo de destino é importado.  
  
 `tdImport`  
 [in] Um `mdTypeDef` token que especifica o tipo de destino.  
  
 `pAssemEmit`  
 [in] Um [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface que representa o assembly para o qual o tipo de destino é importado.  
  
 `ptr`  
 [out] O `mdTypeRef` token que é definido no escopo atual para a referência de tipo.  
  
## <a name="remarks"></a>Comentários  
 Antes de chamar o [: Defineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) método, você pode usar o `DefineImportType` método para criar uma referência de tipo, no escopo atual para a classe pai ou a interface pai do membro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
