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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177708"
---
# <a name="imetadataemitdefinefield-method"></a>Método IMetaDataEmit::DefineField
Cria uma definição para um campo com a assinatura de metadados especificada e obtém um token para essa definição de campo.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `td`  
 [em] O `mdTypeDef` token para a classe de fechamento ou interface.  
  
 `szName`  
 [em] O nome de campo em Unicode.  
  
 `dwFieldFlags`  
 [em] Os atributos de campo. Isto é uma `CorFieldAttr` pequena máscara de valores.  
  
 `pvSigBlob`  
 [em] A assinatura de campo como um BLOB.  
  
 `cbSigBlob`  
 [em] A contagem de `pvSigBlob`bytes em .  
  
 `dwCPlusTypeFlag`  
 [em] O `ELEMENT_TYPE_` *\** pelo valor constante. Isso é `CorElementType` um valor. Se não definir um valor constante `ELEMENT_TYPE_END`para o campo, use .  
  
 `pValue`  
 [em] O valor constante para o campo.  
  
 `cchValue`  
 [em] O tamanho nos caracteres `pValue`(Unicode) de .  
  
 `pmd`  
 [fora] O `mdFieldDef` token atribuído.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
