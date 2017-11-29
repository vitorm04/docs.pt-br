---
title: "Structs (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 475d9b96e078270faf6c841a62e6031556e8e539
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="structs-c-programming-guide"></a>Structs (Guia de Programação em C#)
Structs são definidos usando a palavra-chave [struct](../../../csharp/language-reference/keywords/struct.md), por exemplo:  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Na maioria das vezes, os structs compartilham a mesma sintaxe das classes, embora os structs sejam mais limitados que as classes:  
  
-   Dentro de uma declaração de struct, os campos não podem ser inicializados, a menos que sejam declarados como const ou estáticos.  
  
-   Um struct não pode declarar um construtor padrão (um construtor sem parâmetros) ou um finalizador.  
  
-   Os structs são copiados na atribuição. Quando um struct recebe uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia não altera os dados da cópia original. É importante se lembrar disso ao trabalhar com coleções de tipos de valor como dicionário\<string, myStruct>.  
  
-   Structs são tipos de valor e classes são tipos de referência.  
  
-   Diferentemente das classes, os structs podem ser instanciados sem usar um operador `new`.  
  
-   Os structs podem declarar construtores que têm parâmetros.  
  
-   Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe. Todos os structs herdam diretamente do `System.ValueType`, que herda do `System.Object`.  
  
-   Um struct pode implementar interfaces.  
  
-   Um struct pode ser usado como um tipo que permite valor nulo e pode receber um valor nulo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
-   [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Como saber a diferença entre passar um struct e passar uma referência de classe para um método](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Como implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)
