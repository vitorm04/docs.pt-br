---
title: Método IMetaDataEmit::SetEventProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 506e13ad956a01b16e36d8c71737fe0efce4c01b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450325"
---
# <a name="imetadataemitseteventprops-method"></a>Método IMetaDataEmit::SetEventProps
Define ou atualiza o recurso especificado de um evento definido por uma chamada anterior para [IMetaDataEmit::D efineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ev`  
 no O token do evento.  
  
 `dwEventFlags`  
 no Sinalizadores de eventos. Este é um bitmask de valores de `CorEventAttr`.  
  
 `tkEventType`  
 no O token para a classe de evento. Este é um `mdTypeDef` ou um token de `mdTypeRef`.  
  
 `mdAddOn`  
 no O método usado para assinar o evento ou nulo.  
  
 `mdRemoveOn`  
 no O método usado para cancelar a assinatura do evento, ou NULL.  
  
 `mdFire`  
 no O método usado (por uma classe derivada) para gerar o evento.  
  
 `rmdOtherMethods[]`  
 no Uma matriz de tokens para outros métodos associados ao evento. O último elemento da matriz deve ser `mdMethodDefNil`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
