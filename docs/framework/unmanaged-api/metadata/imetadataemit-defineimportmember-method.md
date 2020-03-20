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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175857"
---
# <a name="imetadataemitdefineimportmember-method"></a>Método IMetaDataEmit::DefineImportMember
Cria uma referência ao membro especificado de um tipo ou módulo definido fora do escopo atual e define um token para essa referência.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `pAssemImport`  
 [em] Uma interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) que representa o conjunto a partir do qual o membro-destino é importado.  
  
 `pbHashValue`  
 [em] Uma matriz que contém o hash `pAssemImport`para a montagem especificada por .  
  
 `cbHashValue`  
 [em] O número de bytes na `pbHashValue` matriz.  
  
 `pImport`  
 [em] Uma interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa o escopo de metadados do qual o membro-alvo é importado.  
  
 `mbMember`  
 [em] O token de metadados que especifica o membro-alvo. O token pode `mdMethodDef` ser um token (para um `mdProperty` `mdFieldDef` membro), (para uma propriedade de membro) ou (para um campo de membro).  
  
 `pAssemEmit`  
 [em] Uma interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) que representa o conjunto para o qual o membro-alvo é importado.  
  
 `tkParent`  
 [em] O `mdTypeRef` `mdModuleRef` ou token para o tipo ou módulo, respectivamente, que possui o membro-alvo.  
  
 `pmr`  
 [fora] O `mdMemberRef` token definido no escopo atual para a referência do membro.  
  
## <a name="remarks"></a>Comentários  
 O `DefineImportMember` método procura o membro, `mbMember`especificado por , que é `pImport`definido em outro escopo, especificado por , e recupera suas propriedades. Ele usa essas informações para chamar o método [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) no escopo atual para criar a referência do membro.  
  
 Geralmente, antes de `DefineImportMember` usar o método, você deve criar, no escopo atual, uma referência de tipo ou referência de módulo para a classe, interface ou módulo do membro-alvo. O token de metadados para essa `tkParent` referência é então passado no argumento. Você não precisa criar uma referência ao pai do membro-alvo se ele for resolvido posteriormente pelo compilador ou linker. Resumidamente:  
  
- Se o membro-alvo for um campo ou método, use o [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou o método [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) para criar uma referência de tipo, no escopo atual, para a classe pai do membro ou interface pai.  
  
- Se o membro-alvo for uma variável global ou função global (ou seja, não um membro de uma classe ou interface), use o método [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) para criar uma referência de módulo, no escopo atual, para o módulo pai do membro.  
  
- Se o pai do membro-alvo for resolvido posteriormente pelo compilador ou linker, então passe `mdTokenNil` para dentro `tkParent`. O único cenário em que isso se aplica é quando uma função global ou variável global está sendo importada de um arquivo .obj que será finalmente vinculado ao módulo atual e aos metadados mesclados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
