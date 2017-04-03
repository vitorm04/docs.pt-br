---
title: "Benefícios dos genéricos (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: 23
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
ms.openlocfilehash: e7e80e9c4612facb2ac88405cd1647785df3124f
ms.lasthandoff: 03/13/2017

---
# <a name="benefits-of-generics-c-programming-guide"></a>Benefícios dos genéricos (Guia de Programação em C#)
Os genéricos oferecem a solução para uma limitação em versões anteriores do Common Language Runtime da linguagem C# em que a generalização é realizada por tipos de conversão de e para o tipo base universal <xref:System.Object>. Ao criar uma classe genérica, é possível criar uma coleção fortemente tipada em tempo de compilação.  
  
 As limitações do uso de classes de coleção não genéricas não podem ser demonstradas com a gravação de um pequeno programa que usa a classe de coleção <xref:System.Collections.ArrayList> da biblioteca de classes do .NET Framework. A <xref:System.Collections.ArrayList> é uma classe de coleção altamente conveniente que pode ser usada sem modificações para armazenar qualquer referência ou tipo de valor.  
  
 [!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 Porém, essa conveniência gera um custo. Qualquer referência ou tipo de valor adicionado a uma <xref:System.Collections.ArrayList> passa por uma conversão implícita upcast para <xref:System.Object>. Se os itens forem tipos de valor, será necessário que eles sejam convertidos ao serem adicionados à lista e desconvertidos ao serem recuperados. Tanto a conversão quanto as operações de conversão boxing e unboxing diminuem o desempenho; o efeito das conversões boxing e unboxing podem ser muito significativos em cenários em que é necessário iterar em coleções grandes.  
  
 A outra limitação é a falta de verificação de tipo em tempo de compilação, pois uma <xref:System.Collections.ArrayList> converte tudo para <xref:System.Object>; não é possível evitar que o código de cliente faça algo como isto no tempo de compilação:  
  
 [!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 Embora seja perfeitamente aceitável e por vezes intencional, se você estiver criando uma coleção heterogênea, é mais provável que combinar cadeias de caracteres e `ints` em uma única <xref:System.Collections.ArrayList> seja um erro de programação e esse erro não será detectado até o tempo de execução.  
  
 Nas versões 1.0 e 1.1 da linguagem C#, é possível evitar os perigos do código generalizado em classes de coleção da biblioteca de classes base do .NET Framework somente pela gravação de suas próprias coleções de tipo específico. Claro, como tal classe não é reutilizável para mais de um tipo de dados, os benefícios da generalização serão perdidos e será necessário gravar novamente a classe para cada tipo que será armazenado.  
  
 O que <xref:System.Collections.ArrayList> e outras classes semelhantes precisam é uma maneira de o código de cliente especificar, em uma base por instância, o tipo de dados específico que pretende usar. Isso eliminaria a necessidade do upcast para `T:System.Object` e possibilitaria ao compilador a realização da verificação de tipo. Em outras palavras, <xref:System.Collections.ArrayList> precisa de um parâmetro de tipo. Isso é exatamente o que os genéricos oferecem. Na coleção genérica <xref:System.Collections.Generic.List%601>, no namespace `N:System.Collections.Generic`, a mesma operação de adição de itens à coleção é semelhante a:  
  
 [!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 Para o código de cliente, a única sintaxe adicionada com <xref:System.Collections.Generic.List%601> comparada a <xref:System.Collections.ArrayList> é o argumento de tipo na declaração e instanciação. Como compensação por essa complexidade na codificação, é possível criar uma lista que não só é mais segura do que <xref:System.Collections.ArrayList>, mas também é significativamente mais rápida, especialmente quando os itens da lista são tipos de valor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Conversão Boxing e Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)   
 [Melhores Práticas para Coleções](http://go.microsoft.com/fwlink/?LinkId=112403)
