---
title: "Sintaxe de consulta e sintaxe de m&#233;todo em LINQ (C#) | Microsoft Docs"
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
  - "LINQ [C#], sintaxe de consulta vs. sintaxe de método"
  - "consultas [LINQ in C#], comparações de sintaxe"
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Sintaxe de consulta e sintaxe de m&#233;todo em LINQ (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A maioria das consultas em Language Integrated Query introdutório \([!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]\) documentação são escritos usando a sintaxe de consulta declarativa do LINQ. No entanto, a sintaxe da consulta deve ser traduzida em chamadas de método para .NET common language runtime \(CLR\) quando o código é compilado. Essas chamadas de método chamar os operadores de consulta padrão, que têm nomes como `Where`, `Select`, `GroupBy`, `Join`, `Max`, e `Average`. Você pode chamá\-las diretamente, usando a sintaxe de método em vez da sintaxe de consulta.  
  
 Sintaxe de consulta e sintaxe de método são semanticamente idênticos, mas muitas pessoas acham a sintaxe de consulta mais simples e fácil de ler. Algumas consultas devem ser expressos como chamadas de método. Por exemplo, você deve usar uma chamada de método para expressar uma consulta que recupera o número de elementos que correspondem a uma condição especificada. Você também deve usar uma chamada de método para uma consulta que recupera o elemento que tem o valor máximo em uma sequência de origem. A documentação de referência para os operadores de consulta padrão no <xref:System.Linq> namespace geralmente usa a sintaxe de método. Portanto, mesmo quando começar escrevendo [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas, é útil estar familiarizado com o uso de sintaxe de método em consultas e expressões de consulta próprias.  
  
## Métodos de extensão de operadores de consulta padrão  
 O exemplo a seguir mostra um simples *expressão de consulta* e a consulta equivalente semanticamente gravado como um *consulta com base no método*.  
  
 [!code-cs[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 A saída dos dois exemplos é idêntica. Você pode ver que o tipo da variável de consulta é o mesmo em ambos os formatos: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Para entender a consulta baseada em método, vamos examiná\-lo melhor. No lado direito da expressão, observe que o `where` cláusula agora é expresso como um método de instância de `numbers` tem o tipo de objeto, que, como você deve se lembrar `IEnumerable<int>`. Se você estiver familiarizado com o genérico <xref:System.Collections.Generic.IEnumerable%601> interface, você sabe que ele não tem um `Where` método. No entanto, se você chamar a lista de preenchimento IntelliSense no IDE do Visual Studio, você verá não só um `Where` método, mas muitos outros métodos, como `Select`, `SelectMany`, `Join`, e `Orderby`. Esses são todos os operadores de consulta padrão.  
  
 ![Operadores de consulta padrão no Intellisense](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 Embora parece como se <xref:System.Collections.Generic.IEnumerable%601> foi redefinido para incluir esses métodos adicionais, na verdade, isso não é o caso. Os operadores de consulta padrão são implementados como um novo tipo de método chamado *métodos de extensão*. Métodos de extensão "estendem" um tipo existente; eles podem ser chamados como se fossem métodos de instância no tipo. Os operadores de consulta padrão estendem <xref:System.Collections.Generic.IEnumerable%601> e que é por que você pode escrever `numbers.Where(...)`.  
  
 Para começar a usar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], tudo o que você realmente precisa saber sobre os métodos de extensão é como colocá\-los em escopo em seu aplicativo usando a corrigir `using` diretivas. Isso é explicado adicionalmente em [Como criar um projeto LINQ](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md). Do ponto de vista do aplicativo, um método de extensão e um método de instância normais são os mesmos.  
  
 Para obter mais informações sobre métodos de extensão, consulte [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Para obter mais informações sobre operadores de consulta padrão, consulte [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md). Alguns [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedores, como [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], implementar seus próprios operadores de consulta padrão e métodos de extensão adicionais para outros tipos além <xref:System.Collections.Generic.IEnumerable%601>.  
  
## Expressões lambda  
 No exemplo anterior, observe que a expressão condicional \(`num % 2 == 0`\) é passado como um argumento na linha para o `Where` método: `Where(num => num % 2 == 0).` essa expressão in\-line é chamado de uma expressão lambda. É uma maneira conveniente de escrever um código que teria que ser gravados no formulário mais complicado, como um método anônimo ou um delegado genérico ou uma árvore de expressão. No c\# `=>` é o operador lambda, que é lido como "vai para". O `num` à esquerda do operador é a variável de entrada que corresponde ao `num` na expressão de consulta. O compilador pode inferir o tipo de `num` porque ele sabe que `numbers` é genérico <xref:System.Collections.Generic.IEnumerable%601> tipo. O corpo do lambda é da mesma forma que a expressão na sintaxe da consulta ou em qualquer outra expressão c\# ou instrução; ele pode incluir chamadas de método e outra lógica complexa. O "valor de retorno" é apenas o resultado da expressão.  
  
 Para começar a usar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], você não precisa usar lambdas extensivamente. No entanto, determinadas consultas só podem ser expressa em sintaxe de método e alguns deles requerem expressões lambda. Após você se familiarizar com lambdas, você verá que eles são uma ferramenta poderosa e flexível no seu [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] caixa de ferramentas. Para obter mais informações, consulte [Expressões lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## Composição de consultas  
 No exemplo de código anterior, observe que o `OrderBy` método é invocado usando o operador ponto na chamada para `Where`.`Where` produz uma sequência filtrada e, em seguida, `Orderby` opera em dessa seqüência, classificando\-lo. Como as consultas retornam uma `IEnumerable`, integrá\-los na sintaxe de método por encadear chamadas de método. Isso é o que o compilador faz por trás dos bastidores quando você escreve consultas usando a sintaxe de consulta. E como uma variável de consulta não armazenar os resultados da consulta, você pode modificá\-lo ou usá\-lo como base para uma nova consulta a qualquer momento, mesmo depois que ele foi executado.  
  
## Consulte também  
 [Introdução a LINQ em C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)