---
title: "Funções anônimas (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f0105ad5ee5a97243e9aeda42c9b1842ec15d0e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="anonymous-functions-c-programming-guide"></a>Funções anônimas (Guia de Programação em C#)
Uma função anônima é uma instrução ou expressão "embutida" que pode ser usada em qualquer local em que um tipo delegado é esperado. Você pode usá-la para inicializar um delegado nomeado ou passá-la em vez de um tipo delegado nomeado como um parâmetro de método.  
  
 Há dois tipos de funções anônimas que serão discutidas individualmente nos tópicos a seguir:  
  
-   [Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
-   [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  As expressões lambda podem ser vinculadas a árvores de expressão e também a delegados.  
  
## <a name="the-evolution-of-delegates-in-c"></a>A evolução de delegados em C#  
 No C# 1.0, você criava uma instância de um delegado, inicializando-a explicitamente com um método que era definido em outro local no código. O C# 2.0 introduziu o conceito de métodos anônimos como uma maneira de escrever blocos de instrução sem nome embutidos, que podem ser executados em uma invocação de delegado. O C# 3.0 introduziu as expressões lambda, que são semelhantes ao conceito dos métodos anônimos, mas mais expressivas e concisas. Essas duas funcionalidades são conhecidas coletivamente como *funções anônimas*. Em geral, aplicativos que se destinam à versão 3.5 e posteriores do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] devem usar as expressões lambda.  
  
 O exemplo a seguir demonstra a evolução da criação de delegado, desde o C# 1.0 até o C# 3.0:  
  
 [!code-cs[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instruções, Expressões e Operadores](../../../csharp/programming-guide/statements-expressions-operators/index.md)   
 [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Árvores de Expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)

