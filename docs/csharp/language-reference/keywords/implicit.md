---
title: implicit (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 160d9f7c0d58abd685bf1d799b53cc96a26aebe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215011"
---
# <a name="implicit-c-reference"></a>implicit (Referência de C#)
A palavra-chave `implicit` é usada para declarar um operador de conversão implícita de tipo definido pelo usuário. Use-a para habilitar conversões implícitas entre um tipo definido pelo usuário e outro tipo, se houver garantia de que a conversão não causará perda de dados.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 Com a eliminação de conversões desnecessárias, as conversões implícitas podem melhorar a legibilidade do código-fonte. No entanto, como as conversões implícitas não exigem que os programadores convertam explicitamente de um tipo para outro, é necessário ter cuidado para evitar resultados inesperados. De modo geral, operadores de conversão implícita nunca devem gerar exceções e perder informações, para que possam ser usados com segurança sem conhecimento do programador. Se um operador de conversão não puder atender a esses critérios, ele deve ser marcado como `explicit`. Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [operator (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)  
 [Como implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
