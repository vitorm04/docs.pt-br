---
title: "Método IMetaDataEmit::DefineEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf790ce270565abaf1d91e54c9e3569a50ab3435
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineevent-method"></a>Método IMetaDataEmit::DefineEvent
Cria uma definição para um evento com a assinatura de metadados especificado e obtém um token a definição desse evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O token para a interface ou classe de destino. Isso é uma `mdTypeDef` ou `mdTypeDefNil` token.  
  
 `szEvent`  
 [in] O nome do evento.  
  
 `dwEventFlags`  
 [in] Sinalizadores de evento.  
  
 `tkEventType`  
 [in] O token para a classe de evento. Este é um `mdTypeDef`, um `mdTypeRef`, ou um `mdTokenNil` token.  
  
 `mdAddOn`  
 [in] O método usado para assinar o evento, ou nulo.  
  
 `mdRemoveOn`  
 [in] O método usado para cancelar a assinatura do evento, ou nulo.  
  
 `mdFire`  
 [in] O método usado (por uma classe derivada) para gerar o evento.  
  
 `rmdOtherMethods[]`  
 [in] Uma matriz de tokens de outros métodos associados ao evento. A matriz é encerrada com um `mdMethodDefNil` token.  
  
 `pmdEvent`  
 [out] O token de metadados atribuído ao evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
