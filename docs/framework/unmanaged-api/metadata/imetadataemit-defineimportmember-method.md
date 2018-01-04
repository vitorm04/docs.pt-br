---
title: "Método IMetaDataEmit::DefineImportMember"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineImportMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bbe2c3144372ba66a0b3bad6198aefeeb7e12d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineimportmember-method"></a>Método IMetaDataEmit::DefineImportMember
Cria uma referência ao membro de um módulo que está definido fora do escopo atual e define um token para essa referência ou tipo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
#### <a name="parameters"></a>Parâmetros  
 `pAssemImport`  
 [in] Um [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface que representa o assembly do qual o membro de destino é importado.  
  
 `pbHashValue`  
 [in] Uma matriz que contém o hash para o conjunto especificado por `pAssemImport`.  
  
 `cbHashValue`  
 [in] O número de bytes a `pbHashValue` matriz.  
  
 `pImport`  
 [in] Um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface que representa o escopo de metadados do qual o membro de destino é importado.  
  
 `mbMember`  
 [in] O token de metadados que especifica o membro de destino. O token pode ser um `mdMethodDef` (para um método de membro) `mdProperty` (para uma propriedade de membro), ou `mdFieldDef` (para um campo de membro) token.  
  
 `pAssemEmit`  
 [in] Um [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface que representa o assembly para o qual o membro de destino é importado.  
  
 `tkParent`  
 [in] O `mdTypeRef` ou `mdModuleRef` token para o tipo ou módulo, respectivamente, que possui o membro de destino.  
  
 `pmr`  
 [out] O `mdMemberRef` token que é definido no escopo atual para a referência do membro.  
  
## <a name="remarks"></a>Comentários  
 O `DefineImportMember` método procura o membro especificado por `mbMember`, que é definido em outro escopo, especificado por `pImport`e recuperar suas propriedades. Ele usa essas informações para chamar o [: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) método no escopo atual para criar a referência do membro.  
  
 Em geral, antes de usar o `DefineImportMember` método, você deve criar, no escopo atual, uma referência de tipo ou a referência de módulo para o módulo, interface ou classe pai do membro de destino. O token de metadados para essa referência, em seguida, é passado a `tkParent` argumento. Você não precisa criar uma referência ao pai do membro de destino se ele será resolvido posteriormente pelo compilador ou vinculador. Para resumir:  
  
-   Se o membro de destino é um campo ou método, use o [Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [: Defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) método para criar uma referência de tipo, no escopo atual, para o a classe pai ou interface pai do membro.  
  
-   Se o membro de destino for uma variável ou global função global (ou seja, não um membro de uma classe ou interface), use o [Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) método para criar uma referência de módulo, no escopo atual para o pai do membro módulo.  
  
-   Se o pai do membro de destino será resolvido posteriormente pelo compilador ou vinculador, passe `mdTokenNil` em `tkParent`. O único cenário em que isso se aplica é quando uma função global ou variável global que está sendo importada de um arquivo. obj, por fim, será vinculado no módulo atual e os metadados de mesclagem.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
