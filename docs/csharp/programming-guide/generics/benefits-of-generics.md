---
title: "Benefícios dos genéricos (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f46a328208b49aa33130a020e1a85b6f7aa7d97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="benefits-of-generics-c-programming-guide"></a>Benefícios dos genéricos (Guia de Programação em C#)
Os genéricos oferecem a solução para uma limitação em versões anteriores do Common Language Runtime da linguagem C# em que a generalização é realizada por tipos de conversão de e para o tipo base universal <xref:System.Object>. Ao criar uma classe genérica, é possível criar uma coleção fortemente tipada em tempo de compilação.  
  
 As limitações do uso de classes de coleção não genéricas não podem ser demonstradas com a gravação de um pequeno programa que usa a classe de coleção <xref:System.Collections.ArrayList> da biblioteca de classes do .NET Framework. A <xref:System.Collections.ArrayList> é uma classe de coleção altamente conveniente que pode ser usada sem modificações para armazenar qualquer referência ou tipo de valor.  
  
 [!code-csharp[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 Porém, essa conveniência gera um custo. Qualquer tipo de referência ou valor que é adicionado a um <xref:System.Collections.ArrayList> é implicitamente upcast para <xref:System.Object>. Se os itens forem tipos de valor, será necessário que eles sejam convertidos ao serem adicionados à lista e desconvertidos ao serem recuperados. Tanto a conversão quanto as operações de conversão boxing e unboxing diminuem o desempenho; o efeito das conversões boxing e unboxing podem ser muito significativos em cenários em que é necessário iterar em coleções grandes.  
  
 A outra limitação é a falta de verificação de tipo em tempo de compilação, pois uma <xref:System.Collections.ArrayList> converte tudo para <xref:System.Object>; não é possível evitar que o código cliente faça algo como isto no tempo de compilação:  
  
 [!code-csharp[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 Embora seja perfeitamente aceitável e por vezes intencional, se você estiver criando uma coleção heterogênea, é mais provável que combinar cadeias de caracteres e `ints` em uma única <xref:System.Collections.ArrayList> seja um erro de programação e esse erro não será detectado até o tempo de execução.  
  
 Nas versões 1.0 e 1.1 da linguagem C#, é possível evitar os perigos do código generalizado em classes de coleção da biblioteca de classes base do .NET Framework somente pela gravação de suas próprias coleções de tipo específico. Claro, como tal classe não é reutilizável para mais de um tipo de dados, os benefícios da generalização serão perdidos e será necessário gravar novamente a classe para cada tipo que será armazenado.  
  
 O que <xref:System.Collections.ArrayList> e outras classes semelhantes precisam é uma maneira de o código cliente especificar, em uma base por instância, o tipo de dados específico que pretende usar. Isso eliminaria a necessidade do upcast para `T:System.Object` e possibilitaria ao compilador a realização da verificação de tipo. Em outras palavras, <xref:System.Collections.ArrayList> precisa de um parâmetro de tipo. Isso é exatamente o que os genéricos oferecem. Na coleção genérica <xref:System.Collections.Generic.List%601>, no namespace `N:System.Collections.Generic`, a mesma operação de adição de itens à coleção é semelhante a:  
  
 [!code-csharp[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 Para código cliente, a única sintaxe adicionada com <xref:System.Collections.Generic.List%601> em comparação com <xref:System.Collections.ArrayList> é o argumento de tipo na declaração e na instanciação. Como compensação por essa complexidade na codificação, é possível criar uma lista que não só é mais segura do que <xref:System.Collections.ArrayList>, mas também é significativamente mais rápida, especialmente quando os itens da lista são tipos de valor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Conversão boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
 [Melhores Práticas para Coleções](http://go.microsoft.com/fwlink/?LinkId=112403)
