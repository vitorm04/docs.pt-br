---
title: Método IMetaDataEmit::SetTypeDefProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: 3ab29fc8c983b354ad5088d26c547868940ec70a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447723"
---
# <a name="imetadataemitsettypedefprops-method"></a>Método IMetaDataEmit::SetTypeDefProps
Define recursos de um tipo definido por uma chamada anterior para [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 no Um token `mdTypeDef` obtido da chamada original para [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atributos. Este é um bitmask de valores de `CorTypeAttr`.  
  
 `tkExtends`  
 no O `mdToken` da classe base. Obtido de uma chamada anterior para [IMetaDataEmit::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)ou `null`.  
  
 `rtkImplements[]`  
 no Uma matriz de tokens para as interfaces que esse tipo implementa. Esses tokens `mdTypeRef` são obtidos usando [IMetaDataEmit::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md). O último elemento da matriz deve ser `mdTokenNil`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
