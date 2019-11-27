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
ms.openlocfilehash: f11b374ed0ecbfc137c43fb641ae691237604691
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431523"
---
# <a name="imetadataemitdefineproperty-method"></a>Método IMetaDataEmit::DefineProperty
Cria uma definição de propriedade para o tipo especificado, com o `get` especificado e `set` acessadores de método, e Obtém um token para essa definição de propriedade.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 no O token para a classe ou interface na qual a propriedade está sendo definida.  
  
 `szProperty`  
 no O nome da propriedade.  
  
 `dwPropFlags`  
 no Os sinalizadores de propriedade.  
  
 `pvSig`  
 no A assinatura da propriedade.  
  
 `cbSig`  
 no A contagem de bytes em `pvSig`.  
  
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
 no Uma matriz de outros métodos associados à propriedade. Encerre a matriz com um `mdTokenNil`.  
  
 `pmdProp`  
 fora O token de `mdProperty` atribuído.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
