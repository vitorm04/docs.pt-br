---
title: Executar uma subconsulta em uma operação de agrupamento (LINQ em C#)
description: Como executar uma subconsulta em uma operação de agrupamento usando LINQ em C#.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 514db81b80557a3026589f00177910cc9446c0f4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47193467"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Executar uma subconsulta em uma operação de agrupamento

Este artigo mostra duas maneiras diferentes de criar uma consulta que ordena os dados de origem em grupos e, em seguida, realiza uma subconsulta em cada grupo individualmente. A técnica básica em cada exemplo é agrupar os elementos de origem usando uma *continuação* chamada `newGroup` e, em seguida, gerar uma nova subconsulta de `newGroup`. Essa subconsulta é executada em cada novo grupo criado pela consulta externa. Observe que, nesse exemplo específico, a saída final não é um grupo, mas uma sequência simples de tipos anônimos.  
  
Para obter mais informações sobre como agrupar, consulte [Cláusula group](../language-reference/keywords/group-clause.md).  
  
Para obter mais informações sobre continuações, consulte [into](../language-reference/keywords/into.md). O exemplo a seguir usa uma estrutura de dados na memória como a fonte de dados, mas os mesmos princípios se aplicam a qualquer tipo de fonte de dados do LINQ.  
  
## <a name="example"></a>Exemplo

> [!NOTE]
> Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  

## <a name="see-also"></a>Consulte também

- [LINQ (Consulta Integrada à Linguagem)](index.md)
