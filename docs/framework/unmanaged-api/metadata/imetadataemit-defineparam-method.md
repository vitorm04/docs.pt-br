---
title: Método IMetaDataEmit::DefineParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86711d107636505ab7aa23f0f72f70bd3e27635d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992648"
---
# <a name="imetadataemitdefineparam-method"></a>Método IMetaDataEmit::DefineParam
Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e obtém um token para essa definição de parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `md`  
 [in] O token para o método cujo parâmetro está sendo definido.  
  
 `ulParamSeq`  
 [in] O número de sequência do parâmetro.  
  
 `szName`  
 [in] O nome do parâmetro no Unicode.  
  
 `dwParamFlags`  
 [in] Sinalizadores para o parâmetro. Esse é um bitmask de `CorParamAttr` valores.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** para o valor da constante.  
  
 `pValue`  
 [in] O valor da constante para o parâmetro.  
  
 `cchValue`  
 [in] O tamanho, em caracteres Unicode, de `pValue`.  
  
 `ppd`  
 [out] O `mdParamDef` token atribuído.  
  
## <a name="remarks"></a>Comentários  
 Os valores de sequência no `ulParamSeq` começam com 1 para parâmetros. Um valor de retorno tem um número de sequência igual a 0.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
