---
title: "Como executar jun&#231;&#245;es agrupadas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "junções de grupos [LINQ em C#]"
  - "junções [C#], grupo"
  - "consultas [LINQ in C#], junções"
  - "expressões de consulta [LINQ em C#], junções"
ms.assetid: 31b654c0-77ac-43fa-be11-aa38e14cae2d
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como executar jun&#231;&#245;es agrupadas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A associação de grupo é útil para produzir estruturas de dados hierárquicos.  Pares de cada elemento da coleção primeiro com um conjunto de elementos correlacionados da segunda coleção.  
  
 Por exemplo, uma classe ou uma tabela de banco de dados relacional, denominada o aluno pode conter dois campos: identificação e nome.  Uma tabela de banco de dados relacionais ou segunda classe denominada o curso pode conter dois campos: StudentId e CourseTitle.  Uma associação de grupo desses dados de duas fontes, com base na correspondência de Student.Id e Course.StudentId, agruparia cada aluno com uma coleção de objetos do curso \(que pode estar vazia\).  
  
> [!NOTE]
>  Cada elemento da coleção primeiro aparece no conjunto de resultados de uma associação de grupo, independentemente de se elementos correlacionados encontram\-se na segunda coleção.  No caso onde nenhum elemento correlacionado é encontrado, a seqüência dos elementos correlacionados para esse elemento está vazia.  Portanto, o seletor de resultado tem acesso a todos os elementos da coleção primeiro.  Isso difere do seletor de resultado em uma associação de grupo, que não consegue acessar os elementos da primeira coleção que não têm correspondências na segunda coleção.  
  
 O primeiro exemplo neste tópico mostra como executar uma associação de grupo.  O segundo exemplo mostra como usar uma associação de grupo para criar elementos XML.  
  
## Exemplo  
  
### Exemplo de associação de grupo  
 O exemplo a seguir executa uma associação de grupo de objetos do tipo `Person` e `Pet` com base na `Person` correspondentes a `Pet.Owner` propriedade.  Ao contrário de uma associação de grupo, que produza um par de elementos para cada correspondência, a associação de grupo produz apenas um objeto resultante para cada elemento da primeira coleção, que, neste exemplo, é um `Person` objeto.  Os elementos correspondentes da segunda coleção, que, neste exemplo, são `Pet` objetos, são agrupados em uma coleção.  Finalmente, a função de seletor de resultado cria a um tipo anônimo para cada correspondência que consiste em `Person.FirstName` e uma coleção de `Pet` objetos.  
  
 [!CODE [CsLINQProgJoining#5](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#5)]  
  
## Exemplo  
  
### Associação de grupo para criar o exemplo de XML  
 Associações de grupo são ideais para criação de XML usando [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  O exemplo a seguir é semelhante ao exemplo anterior, exceto que em vez de criar tipos anônimos, a função de seletor de resultado cria elementos XML que representam os objetos associados.  Para obter mais informações sobre o [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], consulte [LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 [!CODE [CsLINQProgJoining#6](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#6)]  
  
## Compilando o código  
  
-   Criar uma nova  **Aplicativo de Console** de projeto em [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  
  
-   Adicione uma referência a System.Core.dll e System.Xml.Linq.dll se eles já não estão referenciados.  
  
-   Incluir o <xref:System.Linq> e <xref:System.Xml.Linq> namespaces.  
  
-   Copie e cole o código do exemplo no arquivo Program. cs, abaixo do `Main` método.  Adicionar uma linha de código para o `Main` método para chamar o método que você colou no.  
  
-   Execute o programa.  
  
## Consulte também  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Operações join](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Como executar junções internas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [Como executar junções externas esquerdas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)   
 [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)