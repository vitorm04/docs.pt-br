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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 99c1decf27685f027d6baa8412bf20fdf693d161
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664016"
---
# <a name="imetadataemitmergeend-method"></a>Método IMetaDataEmit::MergeEnd

Definir o escopo de mesclagens em atual todos os escopos de metadados especificados por um ou mais chamadas anteriores ao [imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>Parâmetros

Esse método não usa parâmetros.

## <a name="remarks"></a>Comentários

Essa rotina aciona a mesclagem real dos metadados, de todos os escopos especificados, precedendo chamadas para de importação `IMetaDataEmit::Merge`, dentro do escopo de saída atual.

As seguintes condições especiais se aplicam a mesclagem:

- Um identificador de versão do módulo (MVID) nunca é importado, pois é exclusivo para os metadados no escopo de importação.

- Nenhuma propriedade de todo o módulo existente é substituída.

  Se as propriedades do módulo já foram definidas para o escopo atual, nenhuma propriedade do módulo é importada. No entanto, se as propriedades do módulo não tiverem sido definidas no escopo atual, eles serão importados apenas uma vez, quando são encontrados pela primeira vez. Se as propriedades do módulo são encontradas novamente, eles são duplicatas. Se os valores de todas as propriedades de módulo (exceto MVID) são comparados e não há duplicatas forem encontradas, um erro será gerado.

- Para definições de tipo (`TypeDef`), sem duplicatas são mescladas no escopo atual. `TypeDef` objetos são verificados quanto à duplicatas em relação a cada *nome de objeto totalmente qualificado* + *GUID* + *número de versão*. Se houver uma correspondência no nome ou GUID, e qualquer um dos dois elementos é diferente, um erro será gerado. Caso contrário, se corresponderem a todos os três itens, `MergeEnd` faz uma verificação superficial para garantir que as entradas são de fato duplicatas; caso contrário, ocorrerá um erro. Essa verificação superficial procura por:

  - As declarações de membro mesmo, que ocorrem na mesma ordem. Os membros que são sinalizados como `mdPrivateScope` (consulte a [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração) não estão incluídos nessa verificação; eles são mesclados especialmente.

  - O mesmo layout da classe.

  Isso significa que um `TypeDef` objeto deve sempre ser totalmente e consistente definido em cada escopo de metadados no qual ela é declarada; se suas implementações de membro (para uma classe) são distribuídas entre várias unidades de compilação, a definição completa é igual a presente em cada escopo e não incremental a cada escopo. Por exemplo, se os nomes de parâmetro são relevantes para o contrato, eles deverão ser emitidos da mesma maneira em cada escopo. Se não forem relevantes, elas não devem ser emitidas nos metadados.

  A exceção é que um `TypeDef` objeto pode ter membros incrementais sinalizados como `mdPrivateScope`. Ao encontrar esses, `MergeEnd` incrementalmente, adiciona-os ao escopo atual sem levar em consideração as duplicatas. Como o compilador compreende o escopo particular, o compilador deve ser responsável por impor regras.

- Endereços virtuais (relacionados RVAs) não são importados ou mesclados; o compilador deve emitir novamente essas informações.

- Atributos personalizados são mesclados somente quando o item ao qual eles estão conectados é mesclado. Por exemplo, atributos personalizados associados a uma classe são mesclados quando a classe é encontrada pela primeira vez. Se os atributos personalizados são associados com um `TypeDef` ou `MemberDef` que é específico para a unidade de compilação (por exemplo, o carimbo de hora da compilação de um membro), elas não são mescladas e depende do compilador para remover ou atualizar esses metadados.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** Cor.h

**Biblioteca:** Usado como um recurso em mscoree. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
