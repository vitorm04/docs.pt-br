---
title: Cláusula where – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 4b9a5169baa07f2b0363778afbea64ba34eee1d8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238658"
---
# <a name="where-clause-c-reference"></a>Cláusula where (Referência de C#)
A cláusula `where` é usada em uma expressão de consulta para especificar quais elementos da fonte de dados serão retornados na expressão de consulta. Aplica-se uma condição booliana (*predicate*) para cada elemento de origem (referenciado pela variável de intervalo) e retorna aqueles para os quais a condição especificada for verdadeira. Uma única expressão de consulta pode conter várias cláusulas `where` e uma única cláusula pode conter várias subexpressões de predicado.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a cláusula `where` filtra todos os números, exceto aqueles que são menores que cinco. Se você remover a cláusula `where`, todos os números da fonte de dados serão retornados. A expressão `num < 5` é o predicado aplicado a cada elemento.  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a>Exemplo  
 Dentro de uma única cláusula `where`, você pode especificar tantos predicados quanto necessário usando os operadores [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) e [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md). No exemplo a seguir, a consulta especifica dois predicados para selecionar apenas os números pares que são menores que cinco.  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a>Exemplo  
 Uma cláusula `where` pode conter um ou mais métodos que retornam valores boolianos. No exemplo a seguir, a cláusula `where` usa um método para determinar se o valor atual da variável de intervalo é par ou ímpar.  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a>Comentários  
 A cláusula `where` é um mecanismo de filtragem. Ela pode ser posicionada em quase qualquer lugar em uma expressão de consulta, exceto que ela não pode ser a primeira ou a última cláusula. A cláusula `where` pode aparecer antes ou depois de uma cláusula [group](../../../csharp/language-reference/keywords/group-clause.md) dependendo se você tiver que filtrar os elementos de origem antes ou depois de eles serem agrupados.  
  
 Se um predicado especificado não for válido para os elementos na fonte de dados, o resultado será um erro em tempo de compilação. Essa é uma vantagem da verificação de tipo forte fornecida pelo [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
 Em tempo de compilação, a palavra-chave `where` é convertida em uma chamada para o método de operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A>.  
  
## <a name="see-also"></a>Consulte também

- [Palavras-chave de Consulta (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
- [Cláusula From](../../../csharp/language-reference/keywords/from-clause.md)  
- [Cláusula select](../../../csharp/language-reference/keywords/select-clause.md)  
- [Filtrando Dados](../../programming-guide/concepts/linq/filtering-data.md)  
- [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Introdução a LINQ em C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
