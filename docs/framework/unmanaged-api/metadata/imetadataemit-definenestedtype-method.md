---
title: Método IMetaDataEmit::DefineNestedType
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175805"
---
# <a name="imetadataemitdefinenestedtype-method"></a>Método IMetaDataEmit::DefineNestedType
Cria a assinatura de metadados de `mdTypeDef` uma definição de tipo, retorna um token para esse tipo `tdEncloser` e especifica que o tipo definido é um membro do tipo referenciado pelo parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szTypeDef`  
 [em] O nome do tipo em Unicode.  
  
 `dwTypeDefFlags`  
 [em] `TypeDef` atributos. Isto é uma `CorTypeAttr` pequena máscara de valores.  
  
 `tkExtends`  
 [em] O símbolo da classe base. Isso é `mdTypeDef` um `mdTypeRef` ou um símbolo.  
  
 `rtkImplements`[]  
 [em] Uma matriz de tokens que especificam as interfaces que esta classe ou interface implementa.  
  
 `tdEncloser`  
 [em] O símbolo do tipo de fechamento. O último elemento da `mdTokenNil`matriz deve ser .  
  
 `ptd`  
 [fora] O `mdTypeDef` token atribuído.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
