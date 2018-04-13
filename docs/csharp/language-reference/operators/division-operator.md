---
title: Operador / (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Operador / (Referência de C#)
O operador de divisão (`/`) divide o primeiro operando pelo segundo. Todos os tipos numéricos têm operadores de divisão predefinidos.  
  
## <a name="remarks"></a>Comentários  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `/` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Uma sobrecarga do operador `/` sobrecarrega implicitamente o [operador /=](division-assignment-operator.md).  
  
 Quando você divide dois números inteiros, o resultado sempre é um número inteiro. Por exemplo, o resultado do 7/3 é 2. Para determinar o resto de 7/3, use o operador de resto ([%](../../../csharp/language-reference/operators/modulus-operator.md)). Para obter um quociente como um número racional ou fração, dê ao dividendo ou divisor o tipo `float` ou o tipo `double`. Você poderá atribuir o tipo implicitamente se expressar o dividendo ou divisor como um decimal colocando um dígito à direita do ponto decimal, como mostra o exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
