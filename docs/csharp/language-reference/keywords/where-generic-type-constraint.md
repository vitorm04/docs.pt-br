---
title: "where (restri&#231;&#227;o de tipo gen&#233;rico) (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "whereconstraint"
  - "whereconstraint_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "where (restrição de tipo genérico) [C#]"
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# where (restri&#231;&#227;o de tipo gen&#233;rico) (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em uma definição de tipo genérico, o `where` cláusula é usada para especificar restrições sobre os tipos que podem ser usados como argumentos para um parâmetro de tipo definido em uma declaração genérica.  Por exemplo, você pode declarar uma classe genérica, `MyGenericClass`, de modo que o parâmetro de tipo `T` implementa o <xref:System.IComparable%601> interface:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!NOTE]
>  Para obter mais informações na página onde a cláusula em uma expressão de consulta, consulte [Cláusula where](../../../visual-basic/language-reference/queries/where-clause.md).  
  
 Com restrições de interface, um `where` cláusula pode incluir uma restrição de classe base, que informa que um tipo deve ter especificado como uma classe base de classe \(ou ser a classe em si\) para ser usado como um argumento de tipo para o tipo genérico.  Se tal uma restrição for usada, ele deve aparecer antes de quaisquer outras restrições sobre aquele parâmetro de tipo.  
  
 [!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 O `where` cláusula também pode incluir uma restrição de construtor.  É possível criar uma instância de um parâmetro de tipo usando o operador new; No entanto, para fazê\-lo o parâmetro de tipo deve ser limitado pela restrição de construtor, `new()`.  O  [restrição New \(de\)](../../../csharp/language-reference/keywords/new-constraint.md) permite que o compilador sabe que qualquer argumento de tipo fornecido deve ter um acessíveis sem parâmetros – ou o construtor padrão –.  Por exemplo:  
  
 [!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 O `new()` restrição é exibido por última na `where` cláusula.  
  
 Com vários parâmetros de tipo, use um `where` cláusula para cada parâmetro de tipo, por exemplo:  
  
 [!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 Você também pode anexar restrições digitar parâmetros de métodos genéricos, como este:  
  
```  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 Observe que a sintaxe para descrever as restrições de parâmetro de tipo em delegados é o mesmo que um dos métodos:  
  
```  
delegate T MyDelegate<T>() where T : new()  
```  
  
 Para obter informações sobre representantes genéricos, consulte  [Representantes genéricos](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
 Para obter detalhes sobre a sintaxe e uso de restrições, consulte  [restrições em parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Restrição new](../../../csharp/language-reference/keywords/new-constraint.md)   
 [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)