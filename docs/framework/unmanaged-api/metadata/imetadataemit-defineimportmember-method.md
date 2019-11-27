---
title: Método IMetaDataEmit::DefineImportMember
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
ms.openlocfilehash: 75711b3d87699ff5db21a04351ff0acaccabb5aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431863"
---
# <a name="imetadataemitdefineimportmember-method"></a>Método IMetaDataEmit::DefineImportMember
Cria uma referência ao membro especificado de um tipo ou módulo que é definido fora do escopo atual e define um token para essa referência.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAssemImport`  
 no Uma interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) que representa o assembly do qual o membro de destino é importado.  
  
 `pbHashValue`  
 no Uma matriz que contém o hash para o assembly especificado por `pAssemImport`.  
  
 `cbHashValue`  
 no O número de bytes na matriz de `pbHashValue`.  
  
 `pImport`  
 no Uma interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa o escopo de metadados do qual o membro de destino é importado.  
  
 `mbMember`  
 no O token de metadados que especifica o membro de destino. O token pode ser um `mdMethodDef` (para um método de membro), `mdProperty` (para uma propriedade de membro) ou um token de `mdFieldDef` (para um campo de membro).  
  
 `pAssemEmit`  
 no Uma interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) que representa o assembly no qual o membro de destino é importado.  
  
 `tkParent`  
 no O token de `mdTypeRef` ou `mdModuleRef` para o tipo ou módulo, respectivamente, que é proprietário do membro de destino.  
  
 `pmr`  
 fora O token de `mdMemberRef` que é definido no escopo atual para a referência de membro.  
  
## <a name="remarks"></a>Comentários  
 O método `DefineImportMember` pesquisa o membro, especificado por `mbMember`, que é definido em outro escopo, especificado por `pImport`e recupera suas propriedades. Ele usa essas informações para chamar o método [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) no escopo atual para criar a referência de membro.  
  
 Geralmente, antes de usar o método `DefineImportMember`, você deve criar, no escopo atual, uma referência de tipo ou referência de módulo para a classe pai, a interface ou o módulo do membro de destino. O token de metadados para essa referência é passado no argumento `tkParent`. Você não precisará criar uma referência para o pai do membro de destino se ele for resolvido posteriormente pelo compilador ou vinculador. Para resumir:  
  
- Se o membro de destino for um campo ou método, use o método [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [IMetaDataEmit::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) para criar uma referência de tipo, no escopo atual, para a classe pai ou a interface pai do membro.  
  
- Se o membro de destino for uma variável global ou uma função global (ou seja, não for um membro de uma classe ou interface), use o método [IMetaDataEmit::D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) para criar uma referência de módulo, no escopo atual, para o módulo pai do membro.  
  
- Se o pai do membro de destino for resolvido posteriormente pelo compilador ou vinculador, passe `mdTokenNil` em `tkParent`. O único cenário no qual isso se aplica é quando uma função global ou uma variável global está sendo importada de um arquivo. obj que, por fim, será vinculado ao módulo atual e aos metadados mesclados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
