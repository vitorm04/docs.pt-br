---
title: "Introdu&#231;&#227;o a consultas LINQ (C#) | Microsoft Docs"
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
  - "execução adiada [LINQ]"
  - "LINQ, execução adiada"
  - "LINQ, consultas"
  - "consultas [LINQ], sobre consultas LINQ"
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
caps.latest.revision: 47
caps.handback.revision: 47
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Introdu&#231;&#227;o a consultas LINQ (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um *consulta* é uma expressão que recupera dados de uma fonte de dados. Consultas normalmente são expressas em uma linguagem de consulta especializada. Diferentes idiomas foram desenvolvidos ao longo do tempo para os vários tipos de fontes de dados, por exemplo, SQL para bancos de dados relacionais e o XQuery para XML. Portanto, os desenvolvedores precisaram aprender uma nova linguagem de consulta para cada tipo de fonte de dados ou formato de dados que devem ser compatíveis.[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] simplifica essa situação, oferecendo um modelo consistente para trabalhar com dados em vários tipos de fontes de dados e formatos. Em um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta, está sempre trabalhando com objetos. Use os mesmos padrões de codificação básicos para consultar e transformar dados em documentos XML, bancos de dados SQL [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] conjuntos de dados, coleções do .NET e qualquer outro formato para o qual um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedor está disponível.  
  
## Três partes de uma operação de consulta  
 Todos os [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta operações consistem em três ações distintas:  
  
1.  Obter a fonte de dados.  
  
2.  Crie a consulta.  
  
3.  Execute a consulta.  
  
 O exemplo a seguir mostra como as três partes de uma operação de consulta são expressas em código\-fonte. O exemplo usa uma matriz de inteiros como uma fonte de dados para sua conveniência; No entanto, os mesmos conceitos também se aplicam a outras fontes de dados. Este exemplo é chamado em todo o restante deste tópico.  
  
 [!code-cs[CsLINQGettingStarted#1](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_1.cs)]  
  
 A ilustração a seguir mostra a operação de consulta completa. Em [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] a execução da consulta é diferente da própria consulta; em outras palavras não recuperar os dados apenas criando uma variável de consulta.  
  
 ![Concluir a operação de consulta LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_query.png "LINQ\_Query")  
  
## A fonte de dados  
 No exemplo anterior, como a fonte de dados é uma matriz, ele implicitamente suporta genérica <xref:System.Collections.Generic.IEnumerable%601> interface. Esse fato significa que ele pode ser consultado com [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]. Uma consulta é executada em um `foreach` instrução, e `foreach` requer <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>. Tipos que oferecem suporte a <xref:System.Collections.Generic.IEnumerable%601> ou uma interface derivada como genérica <xref:System.Linq.IQueryable%601> são chamados *tipos consultáveis*.  
  
 Um tipo que podem ser consultado não requer modificação ou tratamento especial para servir como um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fonte de dados. Se a fonte de dados não ainda estiver na memória como um tipo que pode ser consultada, o [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedor deve representá\-lo como tal. Por exemplo, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] carrega um documento XML em um que podem ser consultados <xref:System.Xml.Linq.XElement> tipo:  
  
 [!code-cs[CsLINQGettingStarted#2](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_2.cs)]  
  
 Com [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], primeiro você deve criar um mapeamento relacional de objeto em tempo de design manualmente ou usando o [LINQ to SQL Tools no Visual Studio](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2) no Visual Studio. Você escrever suas consultas em relação os objetos e em tempo de execução [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] gerencia a comunicação com o banco de dados. No exemplo a seguir, `Customers` representa uma tabela específica no banco de dados e o tipo do resultado da consulta, <xref:System.Linq.IQueryable%601>, deriva de <xref:System.Collections.Generic.IEnumerable%601>.  
  
```c#  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
  
```  
  
 Para obter mais informações sobre como criar tipos específicos de fontes de dados, consulte a documentação para os diversos [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedores. No entanto, a regra básica é muito simple: um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fonte de dados é qualquer objeto que oferece suporte o genéricos <xref:System.Collections.Generic.IEnumerable%601> interface ou uma interface que herda dela.  
  
> [!NOTE]
>  Tipos, como <xref:System.Collections.ArrayList> que oferecem suporte a não genérica <xref:System.Collections.IEnumerable> interface também pode ser usada como um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fonte de dados. Para obter mais informações, consulte [Como: consultar um ArrayList com LINQ \(c\#\)](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ%20\(C%23\).md).  
  
##  <a name="query"></a> A consulta  
 A consulta especifica quais informações devem ser recuperadas da fonte de dados ou fontes. Opcionalmente, uma consulta também especifica como essas informações devem ser classificadas agrupadas e moldadas antes que ele é retornado. Uma consulta é armazenada em uma variável de consulta e inicializada com uma expressão de consulta. Para tornar mais fácil escrever consultas, c\# apresentou a nova sintaxe de consulta.  
  
 A consulta no exemplo anterior retorna todos os números pares de matriz de inteiros. A expressão de consulta contém três cláusulas: `from`, `where` e `select`. \(Se você estiver familiarizado com SQL, você deve ter percebido que a ordem das cláusulas é revertida da ordem no SQL.\) O `from` cláusula Especifica a fonte de dados, o `where` cláusula aplica o filtro e o `select` cláusula Especifica o tipo dos elementos retornados. Essas e outras cláusulas de consulta são discutidas detalhadamente o [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md) seção. Por enquanto, o ponto importante é que, em [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], a variável de consulta não faz nada e não retorna nenhum dado. Ele armazena apenas as informações necessárias para produzir os resultados quando a consulta é executada em um momento posterior. Para obter mais informações sobre como as consultas são construídas por trás dos bastidores, consulte [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)[Visão geral de operadores de consulta padrão](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
> [!NOTE]
>  Consultas também podem ser expressos usando sintaxe de método. Para obter mais informações, consulte [Sintaxe de consulta e sintaxe de método em LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## Execução da Consulta  
  
### Execução adiada  
 Conforme mencionado anteriormente, a variável de consulta armazena somente os comandos de consulta. A execução real da consulta é adiada até que você itere sobre a variável de consulta em uma `foreach` instrução. Esse conceito é conhecido como *execução diferida* e é demonstrado no exemplo a seguir:  
  
 [!code-cs[csLinqGettingStarted#4](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_3.cs)]  
  
 O `foreach` instrução também é onde os resultados da consulta são recuperados. Por exemplo, na consulta anterior, a variável de iteração `num` contém cada valor \(um por vez\) na sequência retornada.  
  
 Porque a variável de consulta nunca contém os resultados da consulta, você poderá executá\-lo quantas vezes desejar. Por exemplo, você pode ter um banco de dados que está sendo atualizado continuamente por um aplicativo separado. Em seu aplicativo, você pode criar uma consulta que recupera os dados mais recentes e você pode executá\-lo repetidamente em um intervalo para recuperar resultados diferentes cada vez.  
  
### Forçar a execução imediata  
 Consultas que executam funções de agregação em um intervalo de elementos de origem devem primeiro iterar sobre esses elementos. Exemplos de tais consultas são `Count`, `Max`, `Average`, e `First`. Essas consultas são executadas sem um explícito `foreach` instrução porque a consulta em si deve usar `foreach` para retornar um resultado. Observe também que esses tipos de consultas retornam um único valor, não um `IEnumerable` coleção. A consulta a seguir retorna uma contagem de números pares na matriz de origem:  
  
 [!code-cs[csLinqGettingStarted#5](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_4.cs)]  
  
 Para forçar a execução imediata de qualquer consulta e armazenar em cache seus resultados, você pode chamar o <xref:System.Linq.Enumerable.ToList%2A> ou <xref:System.Linq.Enumerable.ToArray%2A> métodos.  
  
 [!code-cs[csLinqGettingStarted#6](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_5.cs)]  
  
 Você também pode forçar a execução colocando o `foreach` loop imediatamente após a expressão de consulta. No entanto, ao chamar `ToList` ou `ToArray` você também armazenar em cache todos os dados em um único objeto de coleção.  
  
## Consulte também  
 [Introdução a LINQ em C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Instruções passo a passo: escrevendo consultas em C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Instruções passo a passo: escrevendo consultas em C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [foreach, in](../../../../csharp/language-reference/keywords/foreach-in.md)   
 [Palavras\-chave de consulta \(LINQ\)](../../../../csharp/language-reference/keywords/query-keywords.md)