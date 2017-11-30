---
title: "Método IMetaDataEmit::Merge"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Merge
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42ebc188dfecde068ef8e2979970118fee91ec4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitmerge-method"></a>Método IMetaDataEmit::Merge
Adiciona o escopo importado especificado à lista de escopos a serem mesclados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pImport`  
 [in] Um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objeto que identifica o escopo importado a serem mesclados.  
  
 `pIMap`  
 [in] Um ponteiro para um [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objeto que especifica o token remapear.  
  
 `pHandleer`  
 [in] Um ponteiro para um <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown` objeto que especifica os erros.  
  
## <a name="remarks"></a>Comentários  
 Chamar [: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) para disparar a fusão de metadados em um único escopo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
