---
title: "Método IMetaDataEmit::MergeEnd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.MergeEnd
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 265fc007b5817e8dffd5846738a7a0003bbddf9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmergeend-method"></a>Método IMetaDataEmit::MergeEnd
Todos os escopos de metadados especificados por uma ou mais chamadas anteriores para o escopo mesclagens em atual [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa nenhum parâmetro.  
  
## <a name="remarks"></a>Comentários  
 Esta rotina aciona a mesclagem real de metadados, de todos os importar escopo especificado, precedendo chamadas para `IMetaDataEmit::Merge`, para o escopo de saída atual.  
  
 As seguintes condições especiais se aplicam a mala direta:  
  
-   Um identificador de versão de módulo (MVID) nunca é importado, porque ele é exclusivo para os metadados no escopo de importação.  
  
-   Nenhuma propriedade de todo o módulo existente é substituída.  
  
     Se as propriedades do módulo já foram definidas para o escopo atual, nenhuma propriedade do módulo é importada. No entanto, se as propriedades do módulo não tem sido definidas no escopo atual, eles serão importados apenas uma vez, quando eles são encontrados pela primeira vez. Se as propriedades do módulo são encontradas novamente, eles são duplicatas. Se os valores de todas as propriedades de módulo (exceto MVID) são comparados e sem duplicatas forem encontradas, um erro será gerado.  
  
-   Para obter definições de tipo (`TypeDef`), não há duplicatas são mescladas no escopo atual. `TypeDef`objetos são verificados para duplicatas em relação a cada *nome totalmente qualificado do objeto* + *GUID* + *o número de versão*. Se houver uma correspondência no nome ou o GUID e qualquer um dos dois elementos é diferente, um erro será gerado. Caso contrário, se corresponderem a todos os três itens, `MergeEnd` faz uma verificação básica para garantir que as entradas são realmente duplicatas; caso contrário, ocorrerá um erro. Essa verificação superficial procura:  
  
    -   As declarações de membro mesmo, que ocorrem na mesma ordem. Membros que são sinalizados como `mdPrivateScope` (consulte a [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeração) não estão incluídos nessa verificação; elas são mescladas especialmente.  
  
    -   O mesmo layout de classe.  
  
     Isso significa que um `TypeDef` objeto deve sempre ser totalmente e consistente definido em cada escopo de metadados no qual ela é declarada, se suas implementações de membro (para uma classe) são distribuídas entre várias unidades de compilação, a definição completa é considerada presente em cada escopo e não incrementais a cada escopo. Por exemplo, se os nomes de parâmetro são relevantes para o contrato, eles devem ser emitidos da mesma maneira em cada escopo. Se não forem relevantes, eles não devem ser emitidos nos metadados.  
  
     A exceção é que um `TypeDef` objeto pode ter membros incrementais sinalizados como `mdPrivateScope`. Encontrar esses, `MergeEnd` incrementalmente adiciona ao escopo atual sem levar em consideração duplicatas. Como o compilador compreende o escopo particular, o compilador deve ser responsável pela aplicação de regras.  
  
-   Endereços virtuais relativos (RVAs) não são importados ou mesclados. o compilador deve emitir novamente essas informações.  
  
-   Atributos personalizados são mesclados apenas quando o item ao qual eles estão conectados é mesclado. Por exemplo, os atributos personalizados associados a uma classe são mesclados quando a classe é encontrada pela primeira vez. Se os atributos personalizados estão associados um `TypeDef` ou `MemberDef` que é específico à unidade de compilação (como o carimbo de hora da compilação de um membro), elas não são mescladas e cabe ao compilador para remover ou atualizar esses metadados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
