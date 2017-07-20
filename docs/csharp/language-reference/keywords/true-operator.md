---
title: "Operador true (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
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
ms.openlocfilehash: bba35ff8c73d41dac585c4bbb2fa42008735248b
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="true-operator-c-reference"></a>Operador true (Referência de C#)
Retorna o valor [bool](../../../csharp/language-reference/keywords/bool.md) `true` para indicar que um operando é true, caso contrário, retorna `false`.  
  
 Antes do C# 2.0, os operadores `true` e `false` eram usados para criar tipos que permitem valor nulo definidos pelo usuário que eram compatíveis com tipos como `SqlBool`. No entanto, a linguagem agora fornece suporte interno para tipos que permitem valor nulo e, sempre que possível, você deve usá-los em vez de sobrecarregar os operadores `true` e `false`. Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Com boolianos que permitem valor nulo, a expressão `a != b` não é necessariamente igual a `!(a == b)` porque um ou ambos os valores podem ser nulos. Você precisa sobrecarregar os operadores `true` e `false` separadamente para identificar corretamente os valores nulos na expressão. O exemplo a seguir mostra como sobrecarregar e usar os operadores `true` e `false`.  
  
 [!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 Um tipo que sobrecarrega os operadores `true` e `false` pode ser usado para a expressão de controle nas instruções [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md) e [for](../../../csharp/language-reference/keywords/for.md), bem como em [expressões condicionais](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Se um tipo define o operador `true`, ele também deve definir o operador [false](../../../csharp/language-reference/keywords/false.md).  
  
 Um tipo não pode sobrecarregar diretamente os operadores lógicos condicionais ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) e [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)), mas um efeito equivalente poderá ser obtido ao sobrecarregar os operadores lógicos regulares e operadores `true` e `false`.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [false](../../../csharp/language-reference/keywords/false.md)
