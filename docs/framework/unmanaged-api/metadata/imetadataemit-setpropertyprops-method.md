---
title: Método IMetaDataEmit::SetPropertyProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: 0fdec87324d6efa0f911e37573093c19b93c0349
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440542"
---
# <a name="imetadataemitsetpropertyprops-method"></a>Método IMetaDataEmit::SetPropertyProps
Define os recursos armazenados em metadados para uma propriedade definida por uma chamada anterior para o [método definoproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pr`  
 no O token para a propriedade a ser alterada  
  
 `dwPropFlags`  
 no Sinalizadores de propriedade.  
  
 `dwCPlusTypeFlag`  
 no O tipo do valor padrão da propriedade.  
  
 `pValue`  
 no O valor padrão para a propriedade.  
  
 `cchValue`  
 no A contagem de caracteres (Unicode) no `pValue`.  
  
 `mdSetter`  
 no O método que define o valor da propriedade.  
  
 `mdGetter`  
 no O método que obtém o valor da propriedade.  
  
 `rmdOtherMethods[]`  
 no Uma matriz de outros métodos associados à propriedade. Finalize essa matriz com um token `mdTokenNil`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
