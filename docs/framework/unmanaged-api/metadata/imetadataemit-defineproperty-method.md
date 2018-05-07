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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c250a577f2ccdbbfefb35225b880c0e4317db36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefineproperty-method"></a>Método IMetaDataEmit::DefineProperty
Cria uma definição de propriedade para o tipo especificado, com especificado `get` e `set` métodos acessadores e recebe um token para essa definição de propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O token de classe ou interface na qual a propriedade está sendo definida.  
  
 `szProperty`  
 [in] O nome da propriedade.  
  
 `dwPropFlags`  
 [in] Os sinalizadores de propriedade.  
  
 `pvSig`  
 [in] A assinatura de propriedade.  
  
 `cbSig`  
 [in] A contagem de bytes em `pvSig`.  
  
 `dwCPlusTypeFlag`  
 [in] O tipo de valor padrão da propriedade.  
  
 `pValue`  
 [in] O valor padrão para a propriedade.  
  
 `cchValue`  
 [in] A contagem de (Unicode) caracteres `pValue`.  
  
 `mdSetter`  
 [in] O método que define o valor da propriedade.  
  
 `mdGetter`  
 [in] O método que obtém o valor da propriedade.  
  
 `rmdOtherMethods[]`  
 [in] Uma matriz de outros métodos associado à propriedade. Encerrar a matriz com um `mdTokenNil`.  
  
 `pmdProp`  
 [out] O `mdProperty` token atribuído.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
