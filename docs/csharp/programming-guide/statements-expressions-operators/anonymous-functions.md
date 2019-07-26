---
title: Funções anônimas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 4d266584e1867a512e4b61e8839fe948aafb007f
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363920"
---
# <a name="anonymous-functions-c-programming-guide"></a>Funções anônimas (Guia de Programação em C#)

Uma função anônima é uma instrução ou expressão "embutida" que pode ser usada em qualquer local em que um tipo delegado é esperado. Você pode usá-la para inicializar um delegado nomeado ou passá-la em vez de um tipo delegado nomeado como um parâmetro de método.

Você pode usar uma [expressão lambda](lambda-expressions.md) ou um [método anônimo](../../language-reference/operators/delegate-operator.md) para criar uma função anônima. Recomendamos o uso de expressões lambda já que elas fornecem uma maneira mais concisa e expressiva de gravar código embutido. Ao contrário dos métodos anônimos, alguns tipos de expressões lambda podem ser convertidos nos tipos de árvore de expressão.

## <a name="the-evolution-of-delegates-in-c"></a>A evolução de delegados em C\#

 No C# 1.0, você criava uma instância de um delegado, inicializando-a explicitamente com um método que era definido em outro local no código. O C# 2.0 introduziu o conceito de métodos anônimos como uma maneira de escrever blocos de instrução sem nome embutidos, que podem ser executados em uma invocação de delegado. O C# 3.0 introduziu as expressões lambda, que são semelhantes ao conceito dos métodos anônimos, mas mais expressivas e concisas. Essas duas funcionalidades são conhecidas coletivamente como *funções anônimas*. Em geral, aplicativos que se destinam à versão 3.5 e posteriores do .NET Framework devem usar as expressões lambda.  
  
 O exemplo a seguir demonstra a evolução da criação de delegado, desde o C# 1.0 até o C# 3.0:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Consulte também

- [Instruções, expressões e operadores](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Delegados](../../../csharp/programming-guide/delegates/index.md)
- [Árvores de expressão (C#)](../concepts/expression-trees/index.md)
