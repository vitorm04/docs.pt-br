---
title: Método IMetaDataImport::GetMethodSemantics
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: 0542c518b64764ad27aa00b8d595be1191059436
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437452"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>Método IMetaDataImport::GetMethodSemantics
Obtém sinalizadores que indicam a relação entre o método referenciado pelo token MethodDef especificado e a propriedade emparelhada e o evento referenciado pelo token EventProp especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mb`  
 no Um token MethodDef que representa o método para obter as informações de função semântica para.  
  
 `tkEventProp`  
 no Um token que representa a propriedade emparelhada e o evento para o qual obter a função do método.  
  
 `pdwSemanticsFlags`  
 fora Um ponteiro para os sinalizadores de semântica associados. Esse valor é um bitmask da enumeração [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) .  
  
## <a name="remarks"></a>Comentários  
 O método [IMetaDataEmit::D efineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) define os sinalizadores de semântica de um método.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
