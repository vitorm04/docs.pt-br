---
title: "Express&#245;es de consulta LINQ (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, expressões de consulta LINQ"
  - "expressões [C#], expressões de consulta LINQ"
  - "LINQ [C#], expressões de consulta"
  - "consultas [LINQ in C#], expressões de consulta"
  - "expressões de consulta [LINQ em C#]"
ms.assetid: 40638f19-fb46-4d26-a2d9-a383b48f5ed4
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Express&#245;es de consulta LINQ (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]é o nome de um conjunto de tecnologias com base na integração dos recursos de consulta diretamente para o idioma C\# \(também em Visual Basic e potencialmente qualquer outro.NET language\).  Com [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)], uma consulta agora é uma construção de linguagem de primeira classe, assim como classes, métodos, eventos e assim por diante.  
  
 Para um desenvolvedor que grava consultas, a parte mais visível "integrada à linguagem" de [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] é a expressão de consulta.  Expressões de consulta são escritas em um declarativa  *sintaxe de consulta* introduzido no C\# 3.0.  Usando a sintaxe de consulta, você pode executar mesmo complexos filtragem, classificação e operações de agrupamento em Fonte de Dados com um mínimo de código.  Você usar os mesmos padrões de expressão de consulta básica para consulta e transformar dados em bancos de dados SQL, [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] conjuntos de dados, documentos XML e fluxos, e.NET coleções.  
  
 O exemplo a seguir mostra a operação de consulta completa.  A operação completa inclui a criação de uma fonte de dados, definindo a expressão de consulta e executar a consulta em um `foreach` instrução.  
  
 [!code-cs[csProgGuideLINQ#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
 Para obter mais informações sobre os fundamentos do [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] na C\#, consulte [Introdução a LINQ em C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
## Visão geral da expressão de consulta  
  
-   Expressões de consulta podem ser usadas para consultar e transformar dados de qualquer [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)]\-habilitado a fonte de dados.  Por exemplo, uma única consulta pode recuperar dados de um banco de dados SQL e produzir um fluxo XML como saída.  
  
-   Expressões de consulta são fáceis dominar porque eles usam construções muitos familiares C\# de linguagem.  Para obter mais informações, consulte [Introdução a LINQ em C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
-   As variáveis em uma expressão de consulta são todos fortemente tipadas, embora em muitos casos você não tem que oferecer o tipo explicitamente porque o compilador pode inferir a ele.  Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
-   Uma consulta não é executada até que você pode iterar sobre a variável de consulta em um `foreach` instrução.  Para obter mais informações, consulte [Introdução a consultas LINQ \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   Em tempo de compilação, expressões de consulta são convertidos em chamadas de método do operador de consulta padrão de acordo com a regras definidas na especificação C\#.  Qualquer consulta que pode ser expressos usando a sintaxe de consulta também pode ser expressos usando a sintaxe do método.  No entanto, na maioria dos casos a sintaxe de consulta é mais legível e concisos.  Para obter mais informações, consulte [Especificação da linguagem C\#](../../../visual-basic/reference/language-specification.md) e [Visão geral de operadores de consulta padrão](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
-   Como regra quando você escreve [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] consultas, é recomendável que você use a sintaxe de consulta sempre que possível e a sintaxe do método sempre que necessário.  Há não semântica ou desempenho diferença entre as duas formas diferentes.  Expressões de consulta são geralmente mais legível do que as expressões equivalentes escritas na sintaxe do método.  
  
-   Algumas operações, da consulta, como <xref:System.Linq.Enumerable.Count%2A> ou <xref:System.Linq.Enumerable.Max%2A>, não ter nenhuma cláusula de expressão de consulta equivalente e, portanto, devem ser expressos como uma chamada de método.  Sintaxe do método pode ser combinado com a sintaxe de consulta de várias maneiras.  Para obter mais informações, consulte [Sintaxe de consulta e sintaxe de método em LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
-   Expressões de consulta podem ser compiladas para árvores de expressão ou representantes, dependendo do tipo que a consulta é aplicada a.  <xref:System.Collections.Generic.IEnumerable%601>consultas são compiladas para representantes.  <xref:System.Linq.IQueryable>e <xref:System.Linq.IQueryable%601> consultas são compiladas em árvores de expressão.  Para obter mais informações, consulte [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md).  
  
 A tabela a seguir, lista os tópicos que fornecem informações adicionais sobre as consultas e exemplos de código para tarefas comuns.  
  
|Tópico|Descrição|  
|------------|---------------|  
|[Noções básicas sobre expressões de consulta](../../../csharp/programming-guide/linq-query-expressions/query-expression-basics.md)|Introduz os conceitos fundamentais de consulta e fornece exemplos da sintaxe de consulta C\#.|  
|[Como escrever consultas LINQ em C\#](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)|Fornece exemplos de vários tipos básicos de expressões de consulta.|  
|[Como manipular exceções em expressões de consulta](../Topic/How%20to:%20Handle%20Exceptions%20in%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)|Como e quando mover possível exception\-throwing código fora de uma expressão de consulta.|  
|[Como preencher coleções de objetos a partir de várias fontes \(LINQ\)](../Topic/How%20to:%20Populate%20Object%20Collections%20from%20Multiple%20Sources%20\(LINQ\).md)|Como usar o `select` a instrução para mesclar dados de fontes diferentes em um novo tipo.|  
|[Como agrupar resultados de consultas](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)|Mostra as diferentes maneiras para usar o `group` cláusula.|  
|[Como criar um grupo aninhado](../Topic/How%20to:%20Create%20a%20Nested%20Group%20\(C%23%20Programming%20Guide\).md)|Mostra como criar grupos aninhados.|  
|[Como executar uma subconsulta em uma operação de agrupamento](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)|Mostra como usar uma subexpressão em uma consulta como fonte de dados para uma nova consulta.|  
|[Como agrupar resultados por chaves contíguas](../../../csharp/programming-guide/linq-query-expressions/how-to-group-results-by-contiguous-keys.md)|Mostra como implementar um operador de consulta padrão do thread\-safe que pode executar operações de agrupamento em fontes de dados de fluxo contínuo.|  
|[Como especificar filtros predicados dinamicamente em tempo de execução](../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)|Mostra como fornecer um número arbitrário de valores a serem usados em comparações de igualdade em um `where` cláusula.|  
|[Como armazenar os resultados de uma consulta na memória](../../../csharp/programming-guide/linq-query-expressions/how-to-store-the-results-of-a-query-in-memory.md)|Ilustra como Materializar e armazenar os resultados da consulta sem necessariamente usando um `foreach` loop.|  
|[Como retornar uma consulta de um método](../../../csharp/programming-guide/linq-query-expressions/how-to-return-a-query-from-a-method.md)|Mostra como retornar as variáveis de consulta de métodos e passá\-los para métodos como parâmetros de entrada.|  
|[Como executar operações de junção personalizadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)|Mostra como executar as operações de associação baseadas em qualquer tipo de função de predicado.|  
|[Como unir usando chaves compostas](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)|Mostra como unir duas fontes com base em mais de uma chave correspondente.|  
|[Como ordenar os resultados de uma cláusula join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)|Mostra a ordem de uma seqüência que é produzida por uma operação de associação.|  
|[Como executar junções internas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)|Mostra como executar uma associação interna na [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].|  
|[Como executar junções agrupadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)|Mostra como produzir uma junção agrupada em [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].|  
|[Como executar junções externas esquerdas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)|Mostra como produzir uma junção externa esquerda na [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].|  
|[Como manipular valores nulos em expressões de consulta](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-null-values-in-query-expressions.md)|Mostra como tratar valores nulos em [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] consultas.|  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Instruções passo a passo: escrevendo consultas em C\#](../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Operações LINQ de consulta básica](../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)   
 [Sintaxe de consulta e sintaxe de método em LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)   
 [Visão geral de operadores de consulta padrão](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Palavras\-chave de consulta \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Como funcionam as consultas Linq to Objects](http://go.microsoft.com/fwlink/?LinkId=112389)   
 [de leitura e consultas de escrita](http://go.microsoft.com/fwlink/?LinkId=112391)   
 [o que é uma coleção?](http://go.microsoft.com/fwlink/?LinkId=112394)   
 [Link para tudo: uma lista de provedores LINQ](http://go.microsoft.com/fwlink/?LinkId=112411)