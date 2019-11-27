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
ms.openlocfilehash: 5b4b0682b2bddff96cb3d720900ed3aa39f06f9d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431843"
---
# <a name="imetadataemitdefineimporttype-method"></a>Método IMetaDataEmit::DefineImportType
Cria uma referência ao tipo especificado que é definido fora do escopo atual e define um token para essa referência.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parâmetros  
 `pAssemImport`  
 no Uma interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) que representa o assembly do qual o tipo de destino é importado.  
  
 `pbHashValue`  
 no Uma matriz que contém o hash para o assembly especificado por `pAssemImport`.  
  
 `cbHashValue`  
 no O número de bytes na matriz de `pbHashValue`.  
  
 `pImport`  
 no Uma interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa o escopo de metadados do qual o tipo de destino é importado.  
  
 `tdImport`  
 no Um token `mdTypeDef` que especifica o tipo de destino.  
  
 `pAssemEmit`  
 no Uma interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) que representa o assembly no qual o tipo de destino é importado.  
  
 `ptr`  
 fora O token de `mdTypeRef` que é definido no escopo atual para a referência de tipo.  
  
## <a name="remarks"></a>Comentários  
 Antes de chamar o método [IMetaDataEmit::D efineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) , você pode usar o método `DefineImportType` para criar uma referência de tipo, no escopo atual, para a classe pai ou a interface pai do membro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
