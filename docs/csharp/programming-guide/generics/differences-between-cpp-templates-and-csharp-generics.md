---
title: Diferenças entre modelos C++ e genéricos C# – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: b794666501fb27d2f73a6050f85df3725050982e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589857"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Diferenças entre modelos C++ e genéricos C# (Guia de Programação em C#)
Os modelos C++ e genéricos C# são recursos de linguagem que fornecem o suporte aos tipos parametrizados. No entanto, há várias diferenças entre os dois. No nível de sintaxe, os genéricos C# são uma abordagem mais simples para os tipos parametrizados sem a complexidade de modelos C++. Além disso, o C# não tenta fornecer toda a funcionalidade que os modelos C++ fornecem. No nível da implementação, a principal diferença é que as substituições do tipo genérico do C# são realizadas em tempo de execução e as informações do tipo genérico são preservadas para objetos instanciados. Para obter mais informações, consulte [Genéricos em tempo de execução](./generics-in-the-run-time.md).  
  
 A seguir estão as principais diferenças entre modelos C++ e genéricos C#:  
  
- Os genéricos C# não oferecem a mesma flexibilidade que os modelos C++. Por exemplo, não é possível chamar os operadores aritméticos em uma classe genérica C#, embora seja possível chamar operadores definidos pelo usuário.  
  
- O C# não permite parâmetros de modelo sem tipo, como `template C<int i> {}`.  
  
- O C# não dá suporte à especialização explícita ou seja, uma implementação personalizada de um modelo para um tipo específico.  
  
- O C# não dá suporte à especialização parcial: uma implementação personalizada para um subconjunto dos argumentos de tipo.  
  
- O C# não permite que o parâmetro de tipo a ser usado como a classe base para o tipo genérico.  
  
- O C# não permite que os parâmetros de tipo tenham tipos padrão.  
  
- No C#, um parâmetro de tipo genérico não pode ser genérico, embora os tipos construídos possam ser usados como genéricos. O C++ permite parâmetros de modelo.  
  
- O C++ permite o código que pode não ser válido para todos os parâmetros de tipo no modelo, que é então verificado para o tipo específico usado como o parâmetro de tipo. O C# requer código em uma classe a ser gravada de forma que ele funcionará com qualquer tipo que satisfaça as restrições. Por exemplo, em C++ é possível escrever uma função que usa os operadores aritméticos `+` e `-` em objetos do parâmetro de tipo, que produzirá um erro no momento da instanciação do modelo com um tipo que não dá suporte a esses operadores. O C# não permite isso. Os únicos constructos da linguagem permitidos são os que podem ser deduzidos das restrições.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Introdução aos genéricos](./index.md)
- [Modelos](/cpp/cpp/templates-cpp)
