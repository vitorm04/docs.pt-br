---
title: Interfaces genéricas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 8b09d6cb6ffb36570bacb568547afa57a2e7d9ba
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244226"
---
# <a name="generic-interfaces-c-programming-guide"></a>Interfaces genéricas (Guia de Programação em C#)
Muitas vezes, é útil definir interfaces para classes de coleção genéricas ou para as classe genéricas que representam itens na coleção. Para classes genéricas, prefere-se usar interfaces genéricas, como <xref:System.IComparable%601> em vez de <xref:System.IComparable>, a fim de evitar operações de conversão boxing e unboxing em tipos de valor. A biblioteca de classes .NET Framework define várias interfaces genéricas para uso com as classes de coleção no namespace <xref:System.Collections.Generic>.  
  
 Quando uma interface é especificada como uma restrição em um parâmetro de tipo, somente os tipos que implementam a interface podem ser usados. O exemplo de código a seguir mostra uma classe `SortedList<T>` que deriva da classe `GenericList<T>`. Para obter mais informações, consulte [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>` adiciona a restrição `where T : IComparable<T>`. Isso habilita o método `BubbleSort` em `SortedList<T>` a usar o método genérico <xref:System.IComparable%601.CompareTo%2A> em elementos de lista. Neste exemplo, os elementos de lista são uma classe simples, `Person`, que implementa `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 Várias interfaces podem ser especificadas como restrições em um único tipo, da seguinte maneira:  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 Uma interface pode definir mais de um parâmetro de tipo, da seguinte maneira:  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 As regras de herança que se aplicam às classes também se aplicam às interfaces:  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 Interfaces genéricas poderão herdar de interfaces não genéricas se a interface genérica for contravariante, o que significa que ela usa apenas seu parâmetro de tipo como um valor retornado. Na biblioteca de classes do .NET Framework, <xref:System.Collections.Generic.IEnumerable%601> herda de <xref:System.Collections.IEnumerable> porque <xref:System.Collections.Generic.IEnumerable%601> usa apenas `T` no valor retornado de <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> e no getter de propriedade <xref:System.Collections.Generic.IEnumerator%601.Current%2A>.  
  
 Classes concretas podem implementar interfaces construídas fechadas, da seguinte maneira:  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 Classes genéricas podem implementar interfaces genéricas ou interfaces construídas fechadas, contanto que a lista de parâmetros de classe forneça todos os argumentos exigidos pela interface, da seguinte maneira:  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 As regras que controlam a sobrecarga de método são as mesmas para métodos em classes genéricas, structs genéricos ou interfaces genéricas. Para obter mais informações, consulte [Métodos Genéricos](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)  
- [Genéricos](~/docs/standard/generics/index.md)
