---
title: "Como agrupar resultados de consultas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "exemplos da cláusula group [LINQ em C#]"
  - "grupos [LINQ em C#]"
  - "consultas [LINQ in C#], agrupando"
  - "expressões de consulta [LINQ em C#], agrupando"
ms.assetid: ee981053-3392-4245-a8c2-b3730211da0d
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como agrupar resultados de consultas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O agrupamento é um dos mais poderosos recursos de [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].  Os exemplos a seguir mostram como agrupar dados de várias maneiras:  
  
-   Por uma propriedade simples.  
  
-   Pela primeiro carta de uma propriedade de cadeia de caracteres.  
  
-   Por um intervalo numérico computado.  
  
-   Predicado booleano ou outra expressão.  
  
-   Por uma chave composta.  
  
 Além disso, as duas últimas consultas projeto seus resultados em um novo tipo anônimo que contém somente o aluno 's primeiro e o sobrenome.  Para obter mais informações, consulte o [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md).  
  
## Exemplo  
 Todos os exemplos neste tópico usam as seguintes fontes de dados e classes auxiliares.  
  
 [!code-cs[csProgGuideLINQ#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_1.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como agrupar os elementos de origem, usando uma única propriedade do elemento como a chave de grupo.  Nesse caso, a chave é um `string`, sobrenome do aluno.  Também é possível usar uma subseqüência de caracteres para a chave.  A operação de agrupamento usa o comparador de igualdade padrão para o tipo.  
  
 Cole o seguinte método para o `StudentClass` classe.  Alterar a instrução de chamada na `Main` método para `sc.GroupBySingleProperty()`.  
  
 [!code-cs[csProgGuideLINQ#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_2.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como agrupar os elementos de origem usando algo diferente de uma propriedade do objeto para a chave de grupo.  Neste exemplo, a chave é a primeira letra do sobrenome do aluno.  
  
 Cole o seguinte método para o `StudentClass` classe.  Alterar a instrução de chamada na `Main` método para `sc.GroupBySubstring()`.  
  
 [!code-cs[csProgGuideLINQ#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_3.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como agrupar os elementos de origem usando um intervalo numérico como uma chave de grupo.  A consulta, em seguida, projeta os resultados em um tipo anônimo que contém apenas o nome e sobrenome e o intervalo de percentil ao qual pertence o aluno.  Um tipo anônimo é usado porque não é necessário usar o completo `Student` o objeto para exibir os resultados.  `GetPercentile`Se uma função auxiliar que calcula um percentil baseia a pontuação média do aluno.  O método retorna um número inteiro entre 0 e 10.  
  
 [!code-cs[csProgGuideLINQ#50](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_4.cs)]  
  
 Cole o seguinte método para o `StudentClass` classe.  Alterar a instrução de chamada na `Main` método para `sc.GroupByRange()`.  
  
 [!code-cs[csProgGuideLINQ#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_5.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como agrupar os elementos de origem usando uma expressão de comparação booleanos.  Neste exemplo, a expressão booleana testa se a pontuação média de exame de um aluno é maior do que 75.  Como nos exemplos anteriores, os resultados são projetados para um tipo anônimo porque o elemento de origem completa não é necessária.  Observe que as propriedades de tipo anônimo se tornam propriedades sobre o `Key` membro e podem ser acessados por nome, quando a consulta é executada.  
  
 Cole o seguinte método para o `StudentClass` classe.  Alterar a instrução de chamada na `Main` método para `sc.GroupByBoolean()`.  
  
 [!code-cs[csProgGuideLINQ#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_6.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como usar um tipo anônimo para encapsular uma chave que contém vários valores.  Neste exemplo, o primeiro valor da chave é a primeira letra do sobrenome do aluno.  O segundo valor da chave é um booleano que especifica se o aluno pontuado mais 85 sobre o exame de primeiro.  Você pode solicitar os grupos por qualquer propriedade na chave.  
  
 Cole o seguinte método para o `StudentClass` classe.  Alterar a instrução de chamada na `Main` método para `sc.GroupByCompositeKey()`.  
  
 [!code-cs[csProgGuideLINQ#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_7.cs)]  
  
## Compilando o código  
 Copie e cole cada método que você deseja testar para o `StudentClass` classe.  Adicionar uma instrução de chamada para o método para o `Main` método e pressione F5.  
  
 Quando você adapta esses métodos para seu próprio aplicativo, lembre\-se de que o LINQ requer a versão 3.5 ou 4 da [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], e que o projeto deve conter uma referência a System.Core.dll e o uso de uma diretriz para System. LINQ.  LINQ to SQL, LINQ to XML e LINQ to DataSet tipos requerem adicionais usando as diretivas e referências.  Para obter mais informações, consulte [Como criar um projeto LINQ](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Consulte também  
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.IGrouping%602>   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md)   
 [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Como executar uma subconsulta em uma operação de agrupamento](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)   
 [Como criar um grupo aninhado](../Topic/How%20to:%20Create%20a%20Nested%20Group%20\(C%23%20Programming%20Guide\).md)   
 [Agrupando dados](../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)