---
ms.openlocfilehash: 29b8feb7959c718391b963c8402b97351b93fa49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235117"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Ausência do Moniker da Estrutura de Destino resulta no comportamento da versão 4.0

|   |   |
|---|---|
|Detalhes|Os aplicativos sem um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> aplicado no nível de assembly serão executados automaticamente usando a semântica (quirks) do .NET Framework 4.0. Para garantir a alta qualidade, é recomendável que todos os binários sejam explicitamente atribuídos com um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> indicando a versão do .NET Framework com a qual eles foram criados. Usar um moniker da estrutura de destino em um arquivo de projeto fará com que o MSBuild aplique automaticamente um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>.|
|Sugestão|O <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> deve ser fornecido, seja por meio da adição do atributo diretamente ao assembly ou da especificação de uma estrutura de destino no [arquivo de projeto, seja por meio da GUI das propriedades do projeto do Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Tempo de execução|
