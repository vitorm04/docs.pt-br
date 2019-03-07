---
title: Método IMetaDataEmit::GetSaveSize
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16984fe108abd1cfc01c471bcfc091a805b28e83
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501497"
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
  
## <a name="parameters"></a>Parâmetros  
 `fSave`  
 [in] Um valor igual a [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeração que especifica se deve obter um tamanho aproximado ou preciso. Apenas três valores são válidos: cssAccurate, cssQuick e cssDiscardTransientCAs:  
  
-   cssAccurate retorna Salvar tamanho exato, mas leva mais tempo para calcular.  
  
-   cssQuick retorna um tamanho preenchido para segurança, mas leva menos tempo para calcular.  
  
-   informa ao cssDiscardTransientCAs `GetSaveSize` que ele pode jogar fora descartáveis atributos personalizados.  
  
 `pdwSaveSize`  
 [out] Um ponteiro para o tamanho que é necessário para salvar o arquivo.  
  
## <a name="remarks"></a>Comentários  
 `GetSaveSize` calcula o espaço necessário, em bytes, para salvar o assembly e todos os seus metadados no escopo atual. (Uma chamada para o [imetadataemit:: Savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) método seria emitir esse número de bytes.)  
  
 Se o chamador implementa o [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (por meio de [imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` executará duas passagens sobre os metadados para otimizar e compactá-lo. Caso contrário, nenhuma otimização é executada.  
  
 Se a otimização é executada, a primeira passagem simplesmente classifica as estruturas de metadados para ajustar o desempenho de pesquisas do momento da importação. Esta etapa normalmente resulta na movimentação de registros, com o efeito colateral que os tokens retidos pela ferramenta para referência futura são invalidados. Os metadados não informar o chamador dessas alterações token até após a segunda passagem, no entanto. Na segunda etapa, várias otimizações são executadas que se destinam a reduzir o tamanho geral dos metadados, como otimização ausente (vinculação inicial) `mdTypeRef` e `mdMemberRef` tokens quando a referência é para um tipo ou membro é declarado no escopo de metadados atual. Essa etapa, ocorre outra rodada de mapeamento de token. Após essa etapa, o mecanismo de metadados notifica o chamador por meio de seu `IMapToken` interface, de qualquer tiver alterado os valores de token.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
