---
title: Operador false (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e73113bd37dbb68590267141ad037f78919520bc
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48848056"
---
# <a name="false-operator-c-reference"></a>Operador false (Referência de C#)

Retorna o valor [bool](bool.md) `true` para indicar que um operando é `false`, caso contrário, retorna `false`.

Antes do C# 2.0, os operadores `true` e `false` eram usados para criar tipos que permitem valor nulo definidos pelo usuário que eram compatíveis com tipos como `SqlBool`. No entanto, a linguagem agora fornece suporte interno para tipos que permitem valor nulo e, sempre que possível, você deve usá-los em vez de sobrecarregar os operadores `true` e `false`. Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../programming-guide/nullable-types/index.md).

Com boolianos que permitem valor nulo, a expressão `a != b` não é necessariamente igual a `!(a == b)` porque um ou ambos os valores podem ser nulos. Você deve sobrecarregar os operadores `true` e `false` separadamente para manipular corretamente os valores nulos na expressão. O exemplo a seguir mostra como sobrecarregar e usar os operadores `true` e `false`.

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

Um tipo que sobrecarrega os operadores `true` e `false` pode ser usado para a expressão de controle nas instruções [if](if-else.md), [do](do.md), [while](while.md) e [for](for.md), bem como em [expressões condicionais](../operators/conditional-operator.md).

Se um tipo define o operador `false`, ele também deve definir o operador [true](true.md).

Um tipo não pode sobrecarregar diretamente os operadores lógicos condicionais [ && ](../operators/conditional-and-operator.md) e [&#124;&#124;](../operators/conditional-or-operator.md), mas um efeito equivalente poderá ser obtido ao sobrecarregar os operadores lógicos regulares e operadores `true` e `false`.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)  
- [Guia de Programação em C#](../../programming-guide/index.md)  
- [Palavras-chave do C#](index.md)  
- [Operadores do C#](../operators/index.md)  
- [true](true.md)  