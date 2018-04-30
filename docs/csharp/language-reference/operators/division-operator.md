---
title: Operador / (Referência de C#)
ms.date: 04/04/2018
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
ms.openlocfilehash: 5b17d122e3e3f75012e084903b6f8975fb53d46c
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a>Operador / (Referência de C#)
O operador de divisão (`/`) divide o primeiro operando pelo segundo. Todos os tipos numéricos têm operadores de divisão predefinidos.
  
## <a name="remarks"></a>Comentários  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `/` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Uma sobrecarga do operador `/` sobrecarrega implicitamente o [operador /=](division-assignment-operator.md).  
  
 Quando você divide dois números inteiros, o resultado sempre é um número inteiro. Por exemplo, o resultado do 7/3 é 2. Não deve ser confundido com a divisão pelo piso, pois o operador `/` é arredondado no sentido de zero: -7/3 é -2.  
  
 Para obter um quociente como um número racional, use os tipos `float`, `double` ou `decimal`. Há várias maneiras de converter entre [tipos numéricos internos](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
 Para determinar o resto, use o [operador de resto](../../../csharp/language-reference/operators/remainder-operator.md) `%`.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
