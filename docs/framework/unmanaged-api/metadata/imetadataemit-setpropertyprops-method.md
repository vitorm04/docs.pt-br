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
ms.openlocfilehash: dc6375f3e2cff1a744a8ff2e6a6adab27bbf8af3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177474"
---
# <a name="imetadataemitsetpropertyprops-method"></a>Método IMetaDataEmit::SetPropertyProps
Define os recursos armazenados em metadados para uma propriedade definida por uma chamada anterior para [DefinirMétodo de Propriedade](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).  
  
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
  
## <a name="parameters"></a>parâmetros  
 `pr`  
 [em] O símbolo para que a propriedade seja alterada  
  
 `dwPropFlags`  
 [em] Bandeiras de propriedade.  
  
 `dwCPlusTypeFlag`  
 [em] O tipo de valor padrão da propriedade.  
  
 `pValue`  
 [em] O valor padrão da propriedade.  
  
 `cchValue`  
 [em] A contagem de caracteres `pValue`(Unicode) em .  
  
 `mdSetter`  
 [em] O método que define o valor da propriedade.  
  
 `mdGetter`  
 [em] O método que obtém o valor da propriedade.  
  
 `rmdOtherMethods[]`  
 [em] Uma série de outros métodos associados à propriedade. Termine esta matriz `mdTokenNil` com um token.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
