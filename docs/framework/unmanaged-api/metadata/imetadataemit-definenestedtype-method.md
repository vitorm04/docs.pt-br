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
ms.openlocfilehash: 5d985e22ba77053127610445374b8c13ca6b97f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431711"
---
# <a name="imetadataemitdefinenestedtype-method"></a>Método IMetaDataEmit::DefineNestedType
Cria a assinatura de metadados de uma definição de tipo, retorna um token `mdTypeDef` para esse tipo e especifica que o tipo definido é um membro do tipo referenciado pelo parâmetro `tdEncloser`.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `szTypeDef`  
 no O nome do tipo em Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atributos. Este é um bitmask de valores de `CorTypeAttr`.  
  
 `tkExtends`  
 no O token da classe base. Este é um `mdTypeDef` ou um token de `mdTypeRef`.  
  
 `rtkImplements`[]  
 no Uma matriz de tokens que especificam as interfaces que essa classe ou interface implementa.  
  
 `tdEncloser`  
 no O token do tipo delimitador. O último elemento da matriz deve ser `mdTokenNil`.  
  
 `ptd`  
 fora O token de `mdTypeDef` atribuído.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
