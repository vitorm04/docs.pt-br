---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234596"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>A versão do Entity Framework deve corresponder à versão do .NET Framework

|   |   |
|---|---|
|Detalhes|A versão do Entity Framework deve corresponder à versão do .NET Framework. O Entity Framework 5 é recomendado para o .NET Framework 4.5. Há alguns problemas conhecidos com o EF 4.x em um projeto do .NET Framework 4.5 em relação a <xref:System.ComponentModel.DataAnnotations>. No .NET 4.5, eles foram movidos para um assembly diferente, portanto, há problemas para determinar quais anotações para usar.|
|Sugestão|Atualização para o Entity Framework 5 do .NET Framework 4.5|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Redirecionando|
