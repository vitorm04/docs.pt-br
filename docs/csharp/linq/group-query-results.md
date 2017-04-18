---
title: Agrupar resultados de consultas
description: Como agrupar resultados.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ee1ad2d65fda8a524b42f44f893e0b6f5f81eea5
ms.lasthandoff: 03/13/2017

---
# <a name="group-query-results"></a>Agrupar resultados de consultas

O agrupamento é um dos recursos mais poderosos do LINQ. Os exemplos a seguir mostram como agrupar dados de várias maneiras:  
  
-   Por uma única propriedade.  
  
-   Pela primeira letra de uma propriedade de cadeia de caracteres.  
  
-   Por um intervalo numérico calculado.  
  
-   Por predicado booliano ou outra expressão.  
  
-   Por uma chave composta.  
  
 Além disso, as duas últimas consultas projetam seus resultados em um novo tipo anônimo que contém somente o primeiro nome e sobrenome do aluno. Para obter mais informações, consulte a [cláusula group](../language-reference/keywords/group-clause.md).  
  
## <a name="example"></a>Exemplo  
 Todos os exemplos neste tópico usam as seguintes fontes de dados e classes auxiliares.  
  
 [!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como agrupar elementos de origem usando uma única propriedade do elemento como a chave de grupo. Nesse caso, a chave é uma `string`, o sobrenome do aluno. Também é possível usar uma subcadeia para a chave. A operação de agrupamento usa o comparador de igualdade padrão para o tipo.  
  
 Cole o seguinte método na classe `StudentClass`. Altere a instrução de chamada no método `Main` para `sc.GroupBySingleProperty()`.  
  
 [!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como agrupar elementos de origem usando algo diferente de uma propriedade do objeto para a chave de grupo. Neste exemplo, a chave é a primeira letra do sobrenome do aluno.  
  
 Cole o seguinte método na classe `StudentClass`. Altere a instrução de chamada no método `Main` para `sc.GroupBySubstring()`.  
  
 [!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como agrupar elementos de origem usando um intervalo numérico como a chave de grupo. Em seguida, a consulta, projeta os resultados em um tipo anônimo que contém apenas o nome e o sobrenome e o intervalo de percentil ao qual o aluno pertence. Um tipo anônimo é usado porque não é necessário usar o objeto `Student` completo para exibir os resultados. `GetPercentile` é uma função auxiliar que calcula um percentil com base na pontuação média do aluno. O método retorna um número inteiro entre 0 e 10.  
  
 [!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 Cole o seguinte método na classe `StudentClass`. Altere a instrução de chamada no método `Main` para `sc.GroupByRange()`.  
  
 [!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como agrupar elementos de origem usando uma expressão de comparação booliana. Neste exemplo, a expressão booliana testa se a pontuação média de provas do aluno é maior que 75. Como nos exemplos anteriores, os resultados são projetados em um tipo anônimo porque o elemento de origem completo não é necessário. Observe que as propriedades no tipo anônimo se tornam propriedades no membro `Key` e podem ser acessadas pelo nome quando a consulta é executada.  
  
 Cole o seguinte método na classe `StudentClass`. Altere a instrução de chamada no método `Main` para `sc.GroupByBoolean()`.  
  
 [!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um tipo anônimo para encapsular uma chave que contém vários valores. Neste exemplo, o primeiro valor da chave é a primeira letra do sobrenome do aluno. O segundo valor da chave é um booliano que especifica se o aluno tirou mais que 85 na primeira prova. Você pode ordenar os grupos por qualquer propriedade na chave.  
  
 Cole o seguinte método na classe `StudentClass`. Altere a instrução de chamada no método `Main` para `sc.GroupByCompositeKey()`.  
  
 [!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.IGrouping%602>   
 [Expressões de Consulta LINQ](index.md)   
 [Cláusula group](../language-reference/keywords/group-clause.md)   
 [Tipos Anônimos](../programming-guide/classes-and-structs/anonymous-types.md)   
 [Executar uma Subconsulta em uma Operação de Agrupamento](perform-a-subquery-on-a-grouping-operation.md)   
 [Criar um Grupo Aninhado](create-a-nested-group.md)   
 [Agrupando Dados](../programming-guide/concepts/linq/grouping-data.md)
