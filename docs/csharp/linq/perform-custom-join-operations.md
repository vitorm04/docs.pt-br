---
title: Executar operações de junção personalizadas (LINQ em C#)
description: Saiba como executar operações de junção personalizadas de LINQ em C#.
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857860"
---
# <a name="perform-custom-join-operations"></a>Executar operações de junção personalizadas

Este exemplo mostra como executar operações de junção que não são possíveis com a cláusula `join`. Em uma expressão de consulta, a cláusula `join` é limitada e otimizada para junções por igualdade, que são, de longe, o tipo de operação de junção mais comum. Ao realizar uma junção por igualdade, provavelmente você terá o melhor desempenho usando a cláusula `join`.

No entanto, a cláusula `join` não pode ser usada nos seguintes casos:

- Quando a junção se baseia em uma expressão de desigualdade (uma junção que não é por igualdade).

- Quando a junção se baseia em mais de uma expressão de igualdade ou desigualdade.

- Quando for necessário introduzir uma variável de intervalo temporária para a sequência do lado direito (interna) antes da operação de junção.

 Para executar junções que não são junções por igualdade, você pode usar várias cláusulas `from` para introduzir cada fonte de dados de forma independente. Em seguida, você aplica uma expressão de predicado em uma cláusula `where` à variável de intervalo para cada fonte. A expressão também pode assumir a forma de uma chamada de método.

> [!NOTE]
> Não confunda esse tipo de operação de junção personalizada com o uso de várias cláusulas `from` para acessar coleções internas. Para obter mais informações, consulte [Cláusula join](../language-reference/keywords/join-clause.md).

## <a name="example"></a>Exemplo

O primeiro método no exemplo a seguir mostra uma união cruzada simples. Uniões cruzadas devem ser usadas com cuidado porque podem produzir conjuntos de resultados muito grandes. No entanto, elas podem ser úteis em alguns cenários para criar sequências de origem em que são executadas consultas adicionais.

O segundo método produz uma sequência de todos os produtos cuja ID da categoria está na lista de categorias no lado esquerdo. Observe o uso da cláusula `let` e do método `Contains` para criar uma matriz temporária. Também é possível criar a matriz antes da consulta e eliminar a primeira cláusula `from`.

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a>Exemplo

No exemplo a seguir, a consulta deve unir duas sequências com base nas chaves correspondentes que, no caso da sequência interna (lado direito), não podem ser obtidas antes da cláusula join. Se essa junção tiver sido executada com uma cláusula `join`, o método `Split` precisará ser chamado para cada elemento. O uso de várias cláusulas `from` permite que a consulta evite a sobrecarga da chamada de método repetida. No entanto, como `join` é otimizado, neste caso em particular ainda pode ser mais rápido do que usar várias cláusulas `from`. Os resultados variam dependendo principalmente do quanto a chamada de método é cara.

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a>Consulte também

- [LINQ (Consulta Integrada à Linguagem)](index.md)
- [Cláusula join](../language-reference/keywords/join-clause.md)
- [Ordenar os resultados de uma cláusula join](order-the-results-of-a-join-clause.md)
