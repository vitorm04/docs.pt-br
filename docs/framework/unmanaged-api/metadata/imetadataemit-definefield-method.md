---
title: Método IMetaDataEmit::DefineField
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432551"
---
# <a name="imetadataemitdefinefield-method"></a>Método IMetaDataEmit::DefineField
Cria uma definição para um campo com a assinatura de metadados especificada e Obtém um token para essa definição de campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 no O token de `mdTypeDef` para a classe ou a interface de circunscrição.  
  
 `szName`  
 no O nome do campo em Unicode.  
  
 `dwFieldFlags`  
 no Os atributos do campo. Este é um bitmask de valores de `CorFieldAttr`.  
  
 `pvSigBlob`  
 no A assinatura de campo como um BLOB.  
  
 `cbSigBlob`  
 no A contagem de bytes em `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 no O `ELEMENT_TYPE_` *\** para o valor constante. Esse é um valor `CorElementType`. Se não estiver definindo um valor constante para o campo, use `ELEMENT_TYPE_END`.  
  
 `pValue`  
 no O valor constante para o campo.  
  
 `cchValue`  
 no O tamanho em caracteres (Unicode) de `pValue`.  
  
 `pmd`  
 fora O token de `mdFieldDef` atribuído.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
