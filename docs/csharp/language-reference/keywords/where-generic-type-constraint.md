---
title: "where (restrição de tipo genérico) (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5c0b9fff370893d890518c6a95a74889b3f2295
ms.lasthandoff: 03/13/2017

---
# <a name="where-generic-type-constraint-c-reference"></a>where (restrição de tipo genérico) (Referência de C#)
Em uma definição de tipo genérico, a cláusula `where` é usada para especificar as restrições nos tipos que podem ser usados como argumentos para um parâmetro de tipo definido em uma declaração genérica. Por exemplo, você pode declarar uma classe genérica, `MyGenericClass`, de modo que o parâmetro de tipo `T` implementa a interface <xref:System.IComparable%601>:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!NOTE]
>  Para obter mais informações sobre a cláusula where em uma expressão de consulta, consulte [Cláusula where](../../../csharp/language-reference/keywords/where-clause.md).  
  
 Além das restrições de interface, uma cláusula `where` pode incluir uma restrição de classe base, que declara que um tipo deve ter a classe especificada como uma classe base (ou ser essa classe em si) para ser usada como um argumento de tipo para o tipo genérico. Se tal restrição for usada, ela deverá aparecer antes de qualquer outra restrição nesse parâmetro de tipo.  
  
 [!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 A cláusula `where` também pode incluir uma restrição de construtor. É possível criar uma instância de um parâmetro de tipo usando o operador new, no entanto, para fazer isso o parâmetro de tipo deve ser restrito pela restrição de construtor, `new()`. A [restrição new()](../../../csharp/language-reference/keywords/new-constraint.md) informa o compilador que qualquer argumento de tipo fornecido deve ter um construtor – ou padrão – sem parâmetros acessível. Por exemplo:  
  
 [!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 A restrição `new()` aparece por último na cláusula `where`.  
  
 Com vários parâmetros de tipo, use uma cláusula `where` para cada parâmetro de tipo, por exemplo:  
  
 [!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 Você também pode anexar restrições aos parâmetros de tipo de métodos genéricos, como esse:  
  
```  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 Observe que a sintaxe para descrever as restrições de parâmetro de tipo em delegados é a mesma que a dos métodos:  
  
```  
delegate T MyDelegate<T>() where T : new()  
```  
  
 Para obter informações sobre delegados genéricos, consulte [Delegados genéricos](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
 Para obter detalhes sobre a sintaxe e o uso de restrições, consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Restrição new](../../../csharp/language-reference/keywords/new-constraint.md)   
 [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
