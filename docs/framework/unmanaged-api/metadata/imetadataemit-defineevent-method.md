---
title: Método IMetaDataEmit::DefineEvent
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175844"
---
# <a name="imetadataemitdefineevent-method"></a>Método IMetaDataEmit::DefineEvent
Cria uma definição para um evento com a assinatura de metadados especificada e obtém um token para essa definição de evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `td`  
 [em] O token para a classe de destino ou interface. Isso é `mdTypeDef` um `mdTypeDefNil` símbolo.  
  
 `szEvent`  
 [em] O nome do evento.  
  
 `dwEventFlags`  
 [em] Bandeiras de eventos.  
  
 `tkEventType`  
 [em] O símbolo para a aula de eventos. Isto `mdTypeDef`é `mdTypeRef`um, `mdTokenNil` a, ou um símbolo.  
  
 `mdAddOn`  
 [em] O método usado para subscrever o evento, ou nulo.  
  
 `mdRemoveOn`  
 [em] O método usado para cancelar a inscrição do evento, ou nulo.  
  
 `mdFire`  
 [em] O método utilizado (por uma classe derivada) para elevar o evento.  
  
 `rmdOtherMethods[]`  
 [em] Uma matriz de tokens para outros métodos associados ao evento. A matriz é encerrada `mdMethodDefNil` com um token.  
  
 `pmdEvent`  
 [fora] O token de metadados atribuído ao evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
