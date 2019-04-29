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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ddbd8c6935f2c0275c132e30ea175c6f198fac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777696"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>Método IMetaDataImport::GetMethodSemantics
Obtém o token de sinalizadores que indica a relação entre o método referenciado pelo token MethodDef especificado e a propriedade emparelhada e o evento referenciado pelo EventProp especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mb`  
 [in] Um token MethodDef que representa o método para obter as informações de função semântica para.  
  
 `tkEventProp`  
 [in] Um token que representa a propriedade emparelhada e o evento para o qual obter a função do método.  
  
 `pdwSemanticsFlags`  
 [out] Um ponteiro para os sinalizadores de semântica associada. Esse valor é um bitmask do [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeração.  
  
## <a name="remarks"></a>Comentários  
 O [imetadataemit:: Defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) método define sinalizadores de semântica do método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
