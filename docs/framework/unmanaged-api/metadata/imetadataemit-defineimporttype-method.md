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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177687"
---
# <a name="imetadataemitdefineimporttype-method"></a>Método IMetaDataEmit::DefineImportType
Cria uma referência ao tipo especificado definido fora do escopo atual e define um token para essa referência.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `pAssemImport`  
 [em] Uma interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) que representa o conjunto a partir do qual o tipo de destino é importado.  
  
 `pbHashValue`  
 [em] Uma matriz que contém o hash `pAssemImport`para a montagem especificada por .  
  
 `cbHashValue`  
 [em] O número de bytes na `pbHashValue` matriz.  
  
 `pImport`  
 [em] Uma interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa o escopo de metadados a partir do qual o tipo de destino é importado.  
  
 `tdImport`  
 [em] Um `mdTypeDef` token que especifica o tipo de destino.  
  
 `pAssemEmit`  
 [em] Uma interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) que representa o conjunto no qual o tipo de destino é importado.  
  
 `ptr`  
 [fora] O `mdTypeRef` token definido no escopo atual para a referência do tipo.  
  
## <a name="remarks"></a>Comentários  
 Antes de chamar o método [IMetaDataEmit::DefineImportMember,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) você pode usar o `DefineImportType` método para criar uma referência de tipo, no escopo atual, para a classe pai do membro ou interface pai.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
