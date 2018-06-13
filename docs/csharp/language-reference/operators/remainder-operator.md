---
title: Operador % (Referência de C#)
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: b906feb22aaec97e58da562b615baae01f3e0719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271060"
---
# <a name="-operator-c-reference"></a>Operador % (Referência de C#)
O operador de resto (`%`) calcula o resto após dividir o primeiro operando pelo segundo. Todos os tipos numéricos têm operadores de restante predefinidos. 
  
## <a name="remarks"></a>Comentários  
 A fórmula `a % b` sempre retornará um valor no intervalo `(-b, b)`, exclusivo (nunca pode retornar `b` ou `-b`), mantendo o sinal do dividendo. Para a divisão de inteiros, o operador de resto satisfaz a regra `a % b = a - (a / b) * b`.
  
 Não deve ser confundido com o módulo canônico, que satisfaz uma regra semelhante, mas com a divisão de piso, e retorna os valores no intervalo `[0, b)`. O C# não tem um operador para o módulo canônico. No entanto, o comportamento é o mesmo para dividendos positivos.
  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `%` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>Comentários  
 Observe os erros de arredondamento associados ao tipo double.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
