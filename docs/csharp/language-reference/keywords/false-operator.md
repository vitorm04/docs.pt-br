---
title: "Operador false (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f9761fb49e2c7f6e4a7615e64cec9fed88318c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="false-operator-c-reference"></a>Operador false (Referência de C#)
Retorna o valor [bool](../../../csharp/language-reference/keywords/bool.md) `true` para indicar que um operando é `false`, caso contrário, retorna `false`.  
  
 Antes do C# 2.0, os operadores `true` e `false` eram usados para criar tipos que permitem valor nulo definidos pelo usuário que eram compatíveis com tipos como `SqlBool`. No entanto, a linguagem agora fornece suporte interno para tipos que permitem valor nulo e, sempre que possível, você deve usá-los em vez de sobrecarregar os operadores `true` e `false`. Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Com boolianos que permitem valor nulo, a expressão `a != b` não é necessariamente igual a `!(a == b)` porque um ou ambos os valores podem ser nulos. Você deve sobrecarregar os operadores `true` e `false` separadamente para manipular corretamente os valores nulos na expressão. O exemplo a seguir mostra como sobrecarregar e usar os operadores `true` e `false`.  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 Um tipo que sobrecarrega os operadores `true` e `false` pode ser usado para a expressão de controle nas instruções [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md) e [for](../../../csharp/language-reference/keywords/for.md), bem como em [expressões condicionais](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Se um tipo define o operador `false`, ele também deve definir o operador [true](../../../csharp/language-reference/keywords/true.md).  
  
 Um tipo não pode sobrecarregar diretamente os operadores lógicos condicionais [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) e [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), mas um efeito equivalente poderá ser obtido ao sobrecarregar os operadores lógicos regulares e operadores `true` e `false`.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
 [true](../../../csharp/language-reference/keywords/true.md)
