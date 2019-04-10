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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8ba8a762c56a666c67b25b9ce0420099fce419a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223518"
---
# <a name="imetadataemitdefinefield-method"></a>Método IMetaDataEmit::DefineField
Cria uma definição para um campo com a assinatura de metadados especificado e obtém um token para essa definição de campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] O `mdTypeDef` token para a classe ou interface delimitador.  
  
 `szName`  
 [in] O nome do campo em Unicode.  
  
 `dwFieldFlags`  
 [in] Os atributos de campo. Esse é um bitmask de `CorFieldAttr` valores.  
  
 `pvSigBlob`  
 [in] A assinatura de campo como um BLOB.  
  
 `cbSigBlob`  
 [in] A contagem de bytes em `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [in] O `ELEMENT_TYPE_` *\** para o valor da constante. Esse é um `CorElementType` valor. Se não definir um valor constante para o campo, use `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] O valor da constante para o campo.  
  
 `cchValue`  
 [in] O tamanho em caracteres (Unicode) do `pValue`.  
  
 `pmd`  
 [out] O `mdFieldDef` token atribuído.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
