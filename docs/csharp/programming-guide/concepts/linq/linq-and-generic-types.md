---
title: "LINQ e tipos gen&#233;ricos (C#) | Microsoft Docs"
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
  - "tipos genéricos [LINQ]"
  - "genéricos [LINQ]"
  - "LINQ [C#], tipos genéricos"
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ e tipos gen&#233;ricos (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas são baseadas em tipos genéricos, que foram introduzidos na versão 2.0 do [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Não é necessário um conhecimento profundo dos genéricos antes de começar a escrever consultas. No entanto, convém entender dois conceitos básicos:  
  
1.  Quando você cria uma instância de uma classe de coleção genérica, como <xref:System.Collections.Generic.List%601>, substitua o "T" com o tipo dos objetos que conterá a lista. Por exemplo, uma lista de cadeias de caracteres é expressa como `List<string>`, e uma lista de `Customer` objetos é expresso como `List<Customer>`. Uma lista genérica tem rigidez de tipos e oferece muitos benefícios em coleções que armazenam seus elementos como <xref:System.Object>. Se você tentar adicionar um `Customer` para um `List<string>`, você obterá um erro em tempo de compilação. É fácil de usar coleções genéricas, porque você não precisa realizar a conversão de tipo de tempo de execução.  
  
2.  <xref:System.Collections.Generic.IEnumerable%601> é a interface que permite que as classes de coleção genérica ser enumerados usando o `foreach` instrução. Classes de coleção genérica suporte <xref:System.Collections.Generic.IEnumerable%601> apenas da coleção não genéricas como classes <xref:System.Collections.ArrayList> suporte <xref:System.Collections.IEnumerable>.  
  
 Para obter mais informações sobre os genéricos, consulte [Genéricos](../../../../visual-basic/reference/command-line-compiler/index.md).  
  
## Variáveis de IEnumerable \< T \> em consultas LINQ  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] variáveis de consulta são digitados como <xref:System.Collections.Generic.IEnumerable%601> ou um tipo derivado como <xref:System.Linq.IQueryable%601>. Quando você vir uma variável de consulta que é digitada como `IEnumerable<Customer>`, simplesmente significa que a consulta, quando ele é executado, produzirá uma sequência de zero ou mais `Customer` objetos.  
  
 [!code-cs[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]  
  
 Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## Permitir que as declarações de tipo genérico de identificador de compilador  
 Se preferir, você pode evitar a sintaxe genérica usando o [var](../../../../csharp/language-reference/keywords/var.md) palavra\-chave. O `var` palavra\-chave instrui o compilador a inferir o tipo de uma variável de consulta examinando a fonte de dados especificada de `from` cláusula. O exemplo a seguir produz o mesmo código compilado do exemplo anterior:  
  
 [!code-cs[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]  
  
 O `var` palavra\-chave é útil quando o tipo da variável é óbvio ou quando não é importante que especificar explicitamente os tipos genéricos aninhados, como aqueles que são produzidos por consultas de grupo. Em geral, é recomendável que se você usar `var`, perceber que isso pode tornar o código mais difícil para outras pessoas ler. Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## Consulte também  
 [Introdução a LINQ em C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Genéricos](../../../../visual-basic/reference/command-line-compiler/index.md)