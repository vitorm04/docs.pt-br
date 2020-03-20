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
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177702"
---
# <a name="imetadataemitdefineparam-method"></a>Método IMetaDataEmit::DefineParam
Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e obtém um token para a definição desse parâmetro.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `md`  
 [em] O token para o método cujo parâmetro está sendo definido.  
  
 `ulParamSeq`  
 [em] O número da seqüência de parâmetros.  
  
 `szName`  
 [em] O nome do parâmetro em Unicode.  
  
 `dwParamFlags`  
 [em] Bandeiras para o parâmetro. Isto é uma `CorParamAttr` pequena máscara de valores.  
  
 `dwCPlusTypeFlag`  
 [em] `ELEMENT_TYPE_` pelo valor *\** constante.  
  
 `pValue`  
 [em] O valor constante para o parâmetro.  
  
 `cchValue`  
 [em] O tamanho, em caracteres `pValue`Unicode, de .  
  
 `ppd`  
 [fora] O `mdParamDef` token atribuído.  
  
## <a name="remarks"></a>Comentários  
 Os valores `ulParamSeq` de seqüência começam com 1 para parâmetros. Um valor de retorno tem um número de seqüência de 0.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
