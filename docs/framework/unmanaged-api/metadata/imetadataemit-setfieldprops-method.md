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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a2c38340614e633de4049515b38cb387031739b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetfieldprops-method"></a>Método IMetaDataEmit::SetFieldProps
Define ou atualiza o valor padrão para o campo referenciado pelo token de campo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fd`  
 [in] O token para o campo de destino.  
  
 `dwFieldFlags`  
 [in] Atributos de campo. Esse é um bitmask de `CorFieldAttr` valores.  
  
 `dwCPlusTypeFlag`  
 [in] O `ELEMENT_TYPE_` *\** para o valor da constante. Este é um `CorElementType` valor. Se uma constante não é definida, defina esse valor como `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] O valor da constante para o campo.  
  
 `cchValue`  
 [in] O tamanho, em caracteres Unicode, de `pValue`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
