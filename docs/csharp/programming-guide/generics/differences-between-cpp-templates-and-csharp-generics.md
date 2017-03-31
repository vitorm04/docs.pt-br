---
title: "Diferenças entre modelos C++ e genéricos C# (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 14
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
ms.openlocfilehash: d3171b1e3f48907778be6e256780e06bad36481f
ms.lasthandoff: 03/13/2017

---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Diferenças entre modelos C++ e genéricos C# (Guia de Programação em C#)
Os modelos C++ e genéricos C# são recursos de linguagem que fornecem o suporte aos tipos parametrizados. No entanto, há várias diferenças entre os dois. No nível de sintaxe, os genéricos C# são uma abordagem mais simples para os tipos parametrizados sem a complexidade de modelos C++. Além disso, o C# não tenta fornecer toda a funcionalidade que os modelos C++ fornecem. No nível da implementação, a principal diferença é que as substituições do tipo genérico do C# são realizadas em tempo de execução e as informações do tipo genérico são preservadas para objetos instanciados. Para obter mais informações, consulte [Genéricos em tempo de execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 A seguir estão as principais diferenças entre modelos C++ e genéricos C#:  
  
-   Os genéricos C# não oferecem a mesma flexibilidade que os modelos C++. Por exemplo, não é possível chamar os operadores aritméticos em uma classe genérica C#, embora seja possível chamar operadores definidos pelo usuário.  
  
-   O C# não permite parâmetros de modelo sem tipo, como `template C<int i> {}`.  
  
-   O C# não dá suporte à especialização explícita ou seja, uma implementação personalizada de um modelo para um tipo específico.  
  
-   O C# não dá suporte à especialização parcial: uma implementação personalizada para um subconjunto dos argumentos de tipo.  
  
-   O C# não permite que o parâmetro de tipo a ser usado como a classe base para o tipo genérico.  
  
-   O C# não permite que os parâmetros de tipo tenham tipos padrão.  
  
-   No C#, um parâmetro de tipo genérico não pode ser genérico, embora os tipos construídos possam ser usados como genéricos. O C++ permite parâmetros de modelo.  
  
-   O C++ permite o código que pode não ser válido para todos os parâmetros de tipo no modelo, que é então verificado para o tipo específico usado como o parâmetro de tipo. O C# requer código em uma classe a ser gravada de forma que ele funcionará com qualquer tipo que satisfaça as restrições. Por exemplo, em C++ é possível escrever uma função que usa os operadores aritméticos `+` e `-` em objetos do parâmetro de tipo, que produzirá um erro no momento da instanciação do modelo com um tipo que não dá suporte a esses operadores. O C# não permite isso. Os únicos constructos da linguagem permitidos são os que podem ser deduzidos das restrições.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Modelos](https://docs.microsoft.com/cpp/cpp/templates-cpp)
