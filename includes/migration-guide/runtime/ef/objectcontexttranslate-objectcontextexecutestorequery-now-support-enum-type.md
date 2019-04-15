---
ms.openlocfilehash: 1d2d6133683360b97569e49402e7c8c4d182b65d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235046"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate e ObjectContext.ExecuteStoreQuery agora dão suporte ao tipo de enumeração

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.0, o parâmetro genérico <code>T</code> dos métodos <code>ObjectContext.Translate</code> e <code>ObjectContext.ExecuteStoreQuery</code> não pode ser uma enumeração. Agora há suporte para esse cenário.|
|Sugestão|Quando Translate ou ExecuteStoreQuery era chamado em um tipo de enumeração no .NET Framework 4.0, '0' era retornado. Se esse comportamento fosse desejável, as chamadas deveriam ser substituídas por uma constante 0 (ou o equivalente de enumeração dele).|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
