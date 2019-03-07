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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 26fd4c89838912e4e07c1d9a8b84aa22f54adeff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501624"
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
  
## <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O token para a interface ou classe de destino. Isso é um `mdTypeDef` ou `mdTypeDefNil` token.  
  
 `szEvent`  
 [in] O nome do evento.  
  
 `dwEventFlags`  
 [in] Sinalizadores de eventos.  
  
 `tkEventType`  
 [in] O token para a classe de evento. Esse é um `mdTypeDef`, um `mdTypeRef`, ou um `mdTokenNil` token.  
  
 `mdAddOn`  
 [in] O método usado para assinar o evento, ou null.  
  
 `mdRemoveOn`  
 [in] O método usado para cancelar a assinatura para o evento, ou nulo.  
  
 `mdFire`  
 [in] O método usado (por uma classe derivada) para gerar o evento.  
  
 `rmdOtherMethods[]`  
 [in] Uma matriz de tokens para outros métodos associados ao evento. A matriz é encerrada com um `mdMethodDefNil` token.  
  
 `pmdEvent`  
 [out] O token de metadados atribuído ao evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
