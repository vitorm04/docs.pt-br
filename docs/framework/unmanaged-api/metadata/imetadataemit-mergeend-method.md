---
title: Método IMetaDataEmit::MergeEnd
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: 34ecfc2f01f22971e135358806adeea632e02f8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448031"
---
# <a name="imetadataemitmergeend-method"></a>Método IMetaDataEmit::MergeEnd

Mescla no escopo atual todos os escopos de metadados especificados por uma ou mais chamadas anteriores para [IMetaDataEmit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).

## <a name="syntax"></a>Sintaxe

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>Parâmetros

Esse método não usa parâmetros.

## <a name="remarks"></a>Comentários

Essa rotina dispara a mesclagem real de metadados, de todos os escopos de importação especificados por chamadas anteriores para `IMetaDataEmit::Merge`, no escopo de saída atual.

As seguintes condições especiais se aplicam à mesclagem:

- Um MVID (identificador de versão do módulo) nunca é importado, pois é exclusivo para os metadados no escopo de importação.

- Nenhuma propriedade existente em todo o módulo é substituída.

  Se as propriedades do módulo já foram definidas para o escopo atual, nenhuma Propriedade do módulo será importada. No entanto, se as propriedades do módulo não tiverem sido definidas no escopo atual, elas serão importadas apenas uma vez, quando forem encontradas. Se essas propriedades de módulo forem encontradas novamente, elas serão duplicadas. Se os valores de todas as propriedades do módulo (exceto MVID) forem comparados e nenhuma duplicata for encontrada, um erro será gerado.

- Para definições de tipo (`TypeDef`), nenhuma duplicata é mesclada no escopo atual. `TypeDef` objetos são verificados em busca de duplicatas em relação a cada *nome de objeto totalmente qualificado* + *GUID* + *número de versão*. Se houver uma correspondência no nome ou GUID, e qualquer um dos outros dois elementos for diferente, um erro será gerado. Caso contrário, se todos os três itens corresponderem, `MergeEnd` uma verificação de cursor para garantir que as entradas sejam de fato duplicatas; caso contrário, um erro será gerado. Esta verificação de cursor procura:

  - As mesmas declarações de membro, que ocorrem na mesma ordem. Os membros sinalizados como `mdPrivateScope` (consulte a enumeração [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) ) não são incluídos nessa verificação; Eles são mesclados especialmente.

  - O mesmo layout de classe.

  Isso significa que um objeto de `TypeDef` sempre deve ser totalmente e consistentemente definido em cada escopo de metadados no qual é declarado; se suas implementações de membro (para uma classe) forem distribuídas entre várias unidades de compilação, a definição completa será considerada como presente em todos os escopos e não incremental para cada escopo. Por exemplo, se os nomes de parâmetros forem relevantes para o contrato, eles deverão ser emitidos da mesma maneira em todos os escopos; Se não forem relevantes, eles não deverão ser emitidos em metadados.

  A exceção é que um objeto `TypeDef` pode ter membros incrementais sinalizados como `mdPrivateScope`. Ao encontrar esses, `MergeEnd` os adiciona incrementalmente ao escopo atual sem considerar duplicatas. Como o compilador compreende o escopo privado, o compilador deve ser responsável por impor regras.

- Os endereços virtuais relativos (RVAs) não são importados ou mesclados; Espera-se que o compilador emita novamente essas informações.

- Os atributos personalizados são mesclados somente quando o item ao qual eles são anexados é mesclado. Por exemplo, os atributos personalizados associados a uma classe são mesclados quando a classe é encontrada pela primeira vez. Se os atributos personalizados estiverem associados a um `TypeDef` ou `MemberDef` que seja específico para a unidade de compilação (como o carimbo de data/hora de uma compilação de membro), eles não serão mesclados e cabe ao compilador remover ou atualizar esses metadados.

## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** Cor. h

**Biblioteca:** Usado como um recurso em MSCorEE. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
