---
title: Método IMetaDataEmit::DefineTypeDef
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf2ca9719cdf62637292bdb39437d36f4b3fcd49
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494396"
---
# <a name="imetadataemitdefinetypedef-method"></a>Método IMetaDataEmit::DefineTypeDef
Cria uma definição de tipo para um tipo common language runtime e obtém um token de metadados para essa definição de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szTypeDef`  
 [in] O nome do tipo em Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atributos. Esse é um bitmask de `CoreTypeAttr` valores.  
  
 `tkExtends`  
 [in] O token da classe base. Ele deve ser um `mdTypeDef` ou um `mdTypeRef` token.  
  
 `rtkImplements`  
 [in] Uma matriz de tokens especificando as interfaces que implementa essa interface ou classe.  
  
 `ptd`  
 [out] O `mdTypeDef` token atribuído.  
  
## <a name="remarks"></a>Comentários  
 Um sinalizador no `dwTypeDefFlags` Especifica se o tipo que está sendo criado é um tipo sistema referência tipo comum (classe ou interface) ou um tipo de valor de sistema de tipo comum.  
  
 Dependendo dos parâmetros fornecidos, esse método, como um efeito colateral, também pode criar um `mdInterfaceImpl` registros para cada interface que é herdada ou implementada por esse tipo. No entanto, esse método não retorna qualquer um desses `mdInterfaceImpl` tokens. Se um cliente deseja posteriormente, adicionar ou modificar uma `mdInterfaceImpl` token, ele deve usar o `IMetaDataImport` interface para enumerá-los. Se você quiser usar semântica COM do `[default]` interface, você deve fornecer a interface padrão como o primeiro elemento no `rtkImplements`; um atributo personalizado definido na classe indicará que a classe tem uma interface padrão (que é sempre considerado como o primeiro `mdInterfaceImpl` token declarado para a classe).  
  
 Cada elemento do `rtkImplements` matriz mantém uma `mdTypeDef` ou `mdTypeRef` token. O último elemento na matriz deve ser `mdTokenNil`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
