---
title: Método IMetaDataEmit::SetFieldProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177550"
---
# <a name="imetadataemitsetfieldprops-method"></a>Método IMetaDataEmit::SetFieldProps
Define ou atualiza o valor padrão para o campo referenciado pelo token de campo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `fd`  
 [em] O símbolo para o campo alvo.  
  
 `dwFieldFlags`  
 [em] Atributos de campo. Isto é uma `CorFieldAttr` pequena máscara de valores.  
  
 `dwCPlusTypeFlag`  
 [em] O `ELEMENT_TYPE_` *\** pelo valor constante. Isso é `CorElementType` um valor. Se uma constante não estiver sendo `ELEMENT_TYPE_END`definida, defina esse valor para .  
  
 `pValue`  
 [em] O valor constante para o campo.  
  
 `cchValue`  
 [em] O tamanho, em caracteres `pValue`Unicode, de .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
