---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774284"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>A versão do Entity Framework deve corresponder à versão do .NET Framework

|   |   |
|---|---|
|Detalhes|A versão do Entity Framework deve corresponder à versão do .NET Framework. O Entity Framework 5 é recomendado para o .NET Framework 4.5. Há alguns problemas conhecidos com o EF 4.x em um projeto do .NET Framework 4.5 em relação a <xref:System.ComponentModel.DataAnnotations>. No .NET 4.5, eles foram movidos para um assembly diferente, portanto, há problemas para determinar quais anotações para usar.|
|Sugestão|Atualização para o Entity Framework 5 do .NET Framework 4.5|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Redirecionando|
