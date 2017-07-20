---
title: "implicit (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 19
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7109a6e467539ca8161b3b44bfb50697314f3c13
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="implicit-c-reference"></a>implicit (Referência de C#)
A palavra-chave `implicit` é usada para declarar um operador de conversão implícita de tipo definido pelo usuário. Use-a para habilitar conversões implícitas entre um tipo definido pelo usuário e outro tipo, se houver garantia de que a conversão não causará perda de dados.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 Com a eliminação de conversões desnecessárias, as conversões implícitas podem melhorar a legibilidade do código-fonte. No entanto, como as conversões implícitas não exigem que os programadores convertam explicitamente de um tipo para outro, é necessário ter cuidado para evitar resultados inesperados. De modo geral, operadores de conversão implícita nunca devem gerar exceções e perder informações, para que possam ser usados com segurança sem conhecimento do programador. Se um operador de conversão não puder atender a esses critérios, ele deve ser marcado como `explicit`. Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [operator (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)   
 [Como implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
