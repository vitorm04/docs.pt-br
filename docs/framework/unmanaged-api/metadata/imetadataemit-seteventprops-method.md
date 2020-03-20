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
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177521"
---
# <a name="imetadataemitseteventprops-method"></a>Método IMetaDataEmit::SetEventProps
Define ou atualiza o recurso especificado de um evento definido por uma chamada anterior ao [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
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
  
## <a name="parameters"></a>parâmetros  
 `ev`  
 [em] O token do evento.  
  
 `dwEventFlags`  
 [em] Bandeiras de eventos. Isto é uma `CorEventAttr` pequena máscara de valores.  
  
 `tkEventType`  
 [em] O símbolo para a aula de eventos. Isso é `mdTypeDef` um `mdTypeRef` ou um símbolo.  
  
 `mdAddOn`  
 [em] O método usado para subscrever o evento, ou nulo.  
  
 `mdRemoveOn`  
 [em] O método usado para cancelar a inscrição do evento, ou nulo.  
  
 `mdFire`  
 [em] O método utilizado (por uma classe derivada) para elevar o evento.  
  
 `rmdOtherMethods[]`  
 [em] Uma matriz de tokens para outros métodos associados ao evento. O último elemento da `mdMethodDefNil`matriz deve ser .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
