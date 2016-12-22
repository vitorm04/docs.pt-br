---
title: "Como executar jun&#231;&#245;es externas esquerdas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "junções externas esquerdas [LINQ em C#]"
  - "[c#], as junções externas esquerdas"
  - "une as expressões de consulta [LINQ em c#]"
  - "consulta de junções [LINQ em c#]"
ms.assetid: 18e32be8-93db-4d30-8dea-ec6596e18f43
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como executar jun&#231;&#245;es externas esquerdas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um left outer join é uma união em que cada elemento da coleção primeiro é retornado, independentemente de se ter quaisquer elementos correlacionados na segunda coleção.  Você pode usar [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] para executar um left outer join chamando o método de <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de um grupo join.  
  
## Exemplo  
 O exemplo seguinte demonstra como usar o método de <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de um grupo join para executar um left outer join.  
  
 A primeira etapa para gerar um left outer join de duas coleções é executar uma inner join usando um grupo join.  \(Consulte [Como executar junções internas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md) para obter uma explicação deste processo.\) Nesse exemplo, a lista de objetos de `Person` interno\- é associado à lista de objetos de `Pet` baseados em um objeto de `Person` que corresponde `Pet.Owner`.  
  
 A segunda etapa é incluir cada elemento da coleção primeiro esquerda \(\) no conjunto de resultados mesmo que o elemento não tem nenhuma correspondência na coleção direita.  Isso é conseguido chamando <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> em cada sequência dos elementos correspondentes do grupo join.  Nesse exemplo, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> é chamado em cada sequência dos objetos de `Pet` .  O método retorna uma coleção que contém um único valor padrão, se a sequência dos objetos de `Pet` está vazia para qualquer objeto de `Person` , garantindo assim que cada objeto de `Person` é representado na coleção de resultado.  
  
> [!NOTE]
>  O valor padrão para um tipo de referência é `null`; como consequência, o exemplo verifica uma referência nula antes de acessar cada elemento de cada coleção de `Pet` .  
  
 [!CODE [CsLINQProgJoining#7](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#7)]  
  
## Compilando o código  
  
-   Crie um novo projeto de aplicativo do console em [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  
  
-   Adicione uma referência a System.Core.dll se já não é referenciado.  
  
-   Inclua o namespace de <xref:System.Linq> .  
  
-   Copie e cole o código de exemplo para o arquivo de module.vb, abaixo do método de `Main` na classe de `Program` .  Adicione uma linha de código para o método de `Main` para chamar o método de `LeftOuterJoinExample` .  
  
-   Executar o programa.  
  
## Consulte também  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Operações join](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [Como executar junções internas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [Como executar junções agrupadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)