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
ms.openlocfilehash: 125a63638a41707b8eed918253cb1f93abb907eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434327"
---
# <a name="imetadataemitgetsavesize-method"></a>Método IMetaDataEmit::GetSaveSize
Obtém o tamanho binário estimado do assembly e seus metadados no escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `fSave`  
 no Um valor da enumeração [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) que especifica se um tamanho preciso ou aproximado deve ser obtido. Somente três valores são válidos: cssAccurate, cssQuick e cssDiscardTransientCAs:  
  
- cssAccurate retorna o tamanho exato da gravação, mas leva mais tempo para calcular.  
  
- cssQuick retorna um tamanho, preenchido para segurança, mas leva menos tempo para calcular.  
  
- cssDiscardTransientCAs informa `GetSaveSize` que ele pode gerar atributos personalizados descartados.  
  
 `pdwSaveSize`  
 fora Um ponteiro para o tamanho necessário para salvar o arquivo.  
  
## <a name="remarks"></a>Comentários  
 `GetSaveSize` calcula o espaço necessário, em bytes, para salvar o assembly e todos os seus metadados no escopo atual. (Uma chamada para o método [IMetaDataEmit:: SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) emitiria esse número de bytes.)  
  
 Se o chamador implementar a interface [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) (por meio de [IMetaDataEmit:: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [IMetaDataEmit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` executará duas passagens sobre os metadados para otimizá-la e compactá-la. Caso contrário, nenhuma otimização será executada.  
  
 Se a otimização for executada, a primeira passagem simplesmente classificará as estruturas de metadados para ajustar o desempenho das pesquisas de tempo de importação. Em geral, essa etapa resulta na movimentação de registros, com o efeito colateral de que os tokens retidos pela ferramenta para referência futura são invalidados. No entanto, os metadados não informam o chamador dessas alterações de token até depois da segunda passagem. Na segunda passagem, são executadas várias otimizações que se destinam a reduzir o tamanho geral dos metadados, como a otimização de `mdTypeRef` (Associação antecipada) e `mdMemberRef` tokens quando a referência é para um tipo ou membro declarado no escopo de metadados atual. Nessa passagem, ocorre outra rodada de mapeamento de token. Após essa passagem, o mecanismo de metadados notifica o chamador, por meio de sua interface de `IMapToken`, de quaisquer valores de token alterados.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
