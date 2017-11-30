---
title: "Método IMetaDataEmit::GetSaveSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9686e8e2c4e8276e725852cb58fac7ed1973778b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgetsavesize-method"></a>Método IMetaDataEmit::GetSaveSize
Obtém o tamanho estimado de binário de assembly e seus metadados no escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fSave`  
 [in] Um valor de [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeração que especifica um tamanho exato ou aproximado. Apenas três valores são válidos: cssAccurate, cssQuick e cssDiscardTransientCAs:  
  
-   cssAccurate retorna Salvar tamanho exato, mas leva mais tempo para calcular.  
  
-   cssQuick retorna um tamanho preenchido para segurança, mas leva menos tempo para calcular.  
  
-   cssDiscardTransientCAs informa `GetSaveSize` que ele pode joga descartáveis atributos personalizados.  
  
 `pdwSaveSize`  
 [out] Um ponteiro para o tamanho que é necessária para salvar o arquivo.  
  
## <a name="remarks"></a>Comentários  
 `GetSaveSize`calcula o espaço necessário, em bytes, para salvar o assembly e todos os seus metadados no escopo atual. (Uma chamada para o [: Savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) método seria emitir esse número de bytes.)  
  
 Se o chamador implementa o [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (por meio de [: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` executará duas passagens sobre os metadados para otimizar e compactá-los. Caso contrário, nenhum otimizações foram executadas.  
  
 Se a otimização é executada, a primeira passagem simplesmente classifica as estruturas de metadados para ajustar o desempenho de pesquisas do momento da importação. Esta etapa normalmente resulta na movimentação de registros, com o efeito colateral que tokens mantidos pela ferramenta para referência futura são invalidados. Os metadados não informar o chamador dessas alterações token até após a segunda etapa, no entanto. Na segunda etapa, várias otimizações são executadas que se destinam para reduzir o tamanho total dos metadados, como otimizar ausente (associação antecipada) `mdTypeRef` e `mdMemberRef` tokens quando a referência é para um tipo ou membro que é declarado no escopo de metadados atual. Essa etapa, ocorre uma nova rodada de mapeamento de token. Após essa etapa, o mecanismo de metadados notifica o chamador por meio de seu `IMapToken` interface, de qualquer alterada valores do token.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
