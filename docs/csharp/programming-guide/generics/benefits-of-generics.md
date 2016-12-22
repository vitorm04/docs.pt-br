---
title: "Benef&#237;cios dos gen&#233;ricos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "genéricos [C#], benefícios"
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Benef&#237;cios dos gen&#233;ricos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os genéricos proporcionam a solução a uma limitação nas versões anteriores do common language runtime e o idioma C\# no qual a generalização é realizada pelos tipos de projeção de e para o tipo base universal <xref:System.Object>.  Criando uma classe genérica, você pode criar uma coleção que é fortemente tipada em tempo de compilação.  
  
 As limitações do uso de classes de coleção não genéricas que podem ser demonstradas escrevendo um pequeno programa que usa a <xref:System.Collections.ArrayList> a classe de coleção da.Biblioteca de classes.  <xref:System.Collections.ArrayList>é uma classe de coleção altamente conveniente que pode ser usada para armazenar qualquer tipo de referência ou valor sem modificação.  
  
 [!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 Mas essa conveniência a um custo.  Qualquer tipo de referência ou valor que é adicionado a uma <xref:System.Collections.ArrayList> é implicitamente elevado para <xref:System.Object>.  Se os itens forem tipos valorados, eles devem ser boxed quando estiverem adicionados à lista e unboxed quando eles são recuperados.  A projeção e operações de boxing e unboxing diminuir o desempenho; o efeito de boxing e unboxing pode ser muito significativo em cenários nos quais você deve itera grandes coleções.  
  
 A outra limitação é a falta de verificação; de tipos em tempo de compilação porque um <xref:System.Collections.ArrayList> projeta que tudo <xref:System.Object>, não há nenhuma maneira em tempo de compilação para impedir que o código de cliente fazendo algo como este:  
  
 [!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 Embora perfeitamente aceitável e às vezes intencional, se você estiver criando um conjunto heterogêneo, combinar seqüências e `ints` em um único <xref:System.Collections.ArrayList> tem mais probabilidade de ser um erro de programação, e esse erro não será detectado até que o tempo de execução.  
  
 Nas versões 1.0 e 1.1 da linguagem C\#, você poderia evitar os perigos do código generalizado em classes de coleção da biblioteca de classes base do .NET Framework apenas escrevendo suas próprias coleções específicas do tipo.  Claro, porque essa classe não é reutilizável para mais de um tipo de dados, você perderá os benefícios da generalização e você tenha que reescrever a classe para cada tipo que será armazenada.  
  
 O que <xref:System.Collections.ArrayList> e outras classes semelhantes realmente precisam é uma forma de código do cliente especificar, em uma base por instância, o tipo de dados específico que pretendem utilizar.  Que eliminaria a necessidade da elevação para `T:System.Object` e seria também tornam possível para o compilador a verificação de tipo.  Em outras palavras, <xref:System.Collections.ArrayList> precisa de um parâmetro de tipo.  É exatamente o que os genéricos proporcionam.  No genérico <xref:System.Collections.Generic.List%601> coleção, na `N:System.Collections.Generic` espaço para nome, a mesma operação de adicionar itens à coleção lembra isto:  
  
 [!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 Para código do cliente, a única adicionado sintaxe com <xref:System.Collections.Generic.List%601> em comparação com <xref:System.Collections.ArrayList> é o argumento de tipo na declaração e instanciação.  Por essa codificação ligeiramente mais complexidade, você pode criar uma lista que não é apenas mais segura do que <xref:System.Collections.ArrayList>, mas também significativamente mais rápido, especialmente quando os itens da lista são os tipos de valor.  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Conversão boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)   
 [Coleções de melhores práticas](http://go.microsoft.com/fwlink/?LinkId=112403)