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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431693"
---
# <a name="imetadataemitdefineparam-method"></a>Método IMetaDataEmit::DefineParam
Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e Obtém um token para essa definição de parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no O token para o método cujo parâmetro está sendo definido.  
  
 `ulParamSeq`  
 no O número de sequência do parâmetro.  
  
 `szName`  
 no O nome do parâmetro em Unicode.  
  
 `dwParamFlags`  
 no Sinalizadores para o parâmetro. Este é um bitmask de valores de `CorParamAttr`.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** para o valor constante.  
  
 `pValue`  
 no O valor da constante para o parâmetro.  
  
 `cchValue`  
 no O tamanho, em caracteres Unicode, de `pValue`.  
  
 `ppd`  
 fora O token de `mdParamDef` atribuído.  
  
## <a name="remarks"></a>Comentários  
 Os valores de sequência em `ulParamSeq` começam com 1 para parâmetros. Um valor de retorno tem um número de sequência de 0.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
