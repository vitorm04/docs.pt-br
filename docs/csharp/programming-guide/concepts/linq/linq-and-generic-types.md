---
title: "LINQ e tipos genéricos (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1951d53b069104f3439aa2fe3ee3975bae0e1659
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-generic-types-c"></a>LINQ e tipos genéricos (C#)
As consultas [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] são baseadas em tipos genéricos, que foram introduzidos na versão 2.0 do [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Não é necessário um conhecimento profundo sobre os genéricos antes de começar a escrever consultas. No entanto, convém entender dois conceitos básicos:  
  
1.  Quando você cria uma instância de uma classe de coleção genérica, como <xref:System.Collections.Generic.List%601>, substitua o "T" pelo tipo dos objetos que a lista conterá. Por exemplo, uma lista de cadeias de caracteres é expressa como `List<string>` e uma lista de objetos `Customer` é expressa como `List<Customer>`. Uma lista genérica é fortemente tipada e oferece muitos benefícios em coleções que armazenam seus elementos como <xref:System.Object>. Se tentar adicionar um `Customer` em uma `List<string>`, você obterá um erro em tempo de compilação. É fácil usar coleções genéricas, porque você não precisa realizar a conversão de tipo em tempo de execução.  
  
2.  A <xref:System.Collections.Generic.IEnumerable%601> é a interface que permite que as classes de coleção genérica sejam enumeradas usando a instrução `foreach`. As classes de coleção genéricas dão suporte à <xref:System.Collections.Generic.IEnumerable%601> assim como as classes de coleção não genéricas, como a <xref:System.Collections.ArrayList>, dão suporte à <xref:System.Collections.IEnumerable>.  
  
 Para obter mais informações sobre os genéricos, consulte [Genéricos](../../../../csharp/programming-guide/generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Variáveis IEnumerable<T\> em consultas LINQ  
 As variáveis de consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] são tipadas como <xref:System.Collections.Generic.IEnumerable%601> ou como um tipo derivado como o <xref:System.Linq.IQueryable%601>. Ao se deparar com uma variável de consulta que é tipada como `IEnumerable<Customer>`, significa apenas que a consulta, quando for executada, produzirá uma sequência de zero ou mais objetos `Customer`.  
  
 [!code-cs[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]  
  
 Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Permitir que o compilador manipule as declarações de tipo genérico  
 Se preferir, poderá evitar a sintaxe genérica, usando a palavra-chave [var](../../../../csharp/language-reference/keywords/var.md). A palavra-chave `var` instrui o compilador a inferir o tipo de uma variável de consulta, examinando a fonte de dados especificada na cláusula `from`. O exemplo a seguir produz o mesmo código compilado que o exemplo anterior:  
  
 [!code-cs[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]  
  
 A palavra-chave `var` é útil quando o tipo da variável for óbvio ou quando não é tão importante especificar explicitamente os tipos genéricos aninhados, como aqueles que são produzidos por consultas de grupo. É recomendável que você note que o código poderá se tornar mais difícil de ser lido por outras pessoas, caso você use a `var`. Para obter mais informações, consulte [Variáveis Locais de Tipo Implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Genéricos](../../../../csharp/programming-guide/generics/index.md)
