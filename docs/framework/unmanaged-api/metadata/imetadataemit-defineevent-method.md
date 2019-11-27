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
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432560"
---
# <a name="imetadataemitdefineevent-method"></a>Método IMetaDataEmit::DefineEvent
Cria uma definição para um evento com a assinatura de metadados especificada e Obtém um token para essa definição de evento.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 no O token para a classe ou interface de destino. É um token `mdTypeDef` ou `mdTypeDefNil`.  
  
 `szEvent`  
 no O nome do evento.  
  
 `dwEventFlags`  
 no Sinalizadores de eventos.  
  
 `tkEventType`  
 no O token para a classe de evento. Este é um `mdTypeDef`, um `mdTypeRef`ou um token `mdTokenNil`.  
  
 `mdAddOn`  
 no O método usado para assinar o evento ou nulo.  
  
 `mdRemoveOn`  
 no O método usado para cancelar a assinatura do evento, ou NULL.  
  
 `mdFire`  
 no O método usado (por uma classe derivada) para gerar o evento.  
  
 `rmdOtherMethods[]`  
 no Uma matriz de tokens para outros métodos associados ao evento. A matriz é encerrada com um token `mdMethodDefNil`.  
  
 `pmdEvent`  
 fora O token de metadados atribuído ao evento.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
