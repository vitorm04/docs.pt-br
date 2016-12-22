---
title: "Como acessar uma classe de cole&#231;&#227;o com foreach (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "classes de coleções [C#], instrução foreach"
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como acessar uma classe de cole&#231;&#227;o com foreach (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O exemplo de código a seguir ilustra como escrever uma classe de coleção não genérico que pode ser usada com  [foreach](../../../csharp/language-reference/keywords/foreach-in.md).  O exemplo define uma classe de tokenizer de seqüência de caracteres.  
  
> [!NOTE]
>  Este exemplo representa a prática recomendada somente quando você não pode usar uma classe de coleção genérica.  Para obter um exemplo de como implementar uma classe de coleção genérica de tipo seguro que ofereça suporte a <xref:System.Collections.Generic.IEnumerable%601>, consulte [Iteradores](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).  
  
 No exemplo, o código a seguir segmento usa a `Tokens` classe para quebrar a frase "Esta é uma frase de exemplo." em tokens usando ' ' e '\-' como separadores.  O código, em seguida, exibe esses tokens usando um `foreach` instrução.  
  
 [!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## Exemplo  
 Internamente, o `Tokens` classe usa uma matriz para armazenar os tokens.  Como as matrizes implementam <xref:System.Collections.IEnumerator> e <xref:System.Collections.IEnumerable>, o exemplo de código poderia ter usado a métodos de enumeração da matriz \(<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, e <xref:System.Collections.IEnumerator.Current%2A>\) em vez de defini\-los na `Tokens` classe.  As definições de método são incluídas no exemplo para esclarecer como são definidas e o que cada um oferece.  
  
 [!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 Em C\#, não é necessário para implementar uma classe de coleção <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> para ser compatível com `foreach`.  Se a classe tem o necessário <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, e <xref:System.Collections.IEnumerator.Current%2A> membros, ele funcionará com `foreach`.  Omitir as interfaces tem a vantagem de permitindo que você defina um tipo de retorno para `Current` que é mais específico do que <xref:System.Object>.  Isso fornece segurança de tipos.  
  
 Por exemplo, altere as seguintes linhas no exemplo anterior.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Porque `Current` retorna uma seqüência de caracteres, o compilador pode detectar quando um tipo incompatível é usado em um `foreach` instrução, como mostrado no código a seguir.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 A desvantagem de omissão <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> é que a classe de coleção não é interoperável com o `foreach` declarações ou instruções equivalentes, de outros idiomas de runtime de linguagem comum.  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)