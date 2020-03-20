---
title: Método IMetaDataEmit::DefineProperty
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175779"
---
# <a name="imetadataemitdefineproperty-method"></a>Método IMetaDataEmit::DefineProperty
Cria uma definição de propriedade para o `get` tipo `set` especificado, com os acessórios especificados e do método, e recebe um token para essa definição de propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `td`  
 [em] O token para classe ou interface na qual a propriedade está sendo definida.  
  
 `szProperty`  
 [em] O nome da propriedade.  
  
 `dwPropFlags`  
 [em] As bandeiras da propriedade.  
  
 `pvSig`  
 [em] A assinatura da propriedade.  
  
 `cbSig`  
 [em] A contagem de `pvSig`bytes em .  
  
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
 [em] Uma série de outros métodos associados à propriedade. Termine a matriz `mdTokenNil`com um .  
  
 `pmdProp`  
 [fora] O `mdProperty` token atribuído.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
