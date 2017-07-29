---
title: "Operador / (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
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
ms.openlocfilehash: 2972261996467f987fa457213b1bcb482d9f1519
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>Operador / (Referência de C#)
O operador de divisão (`/`) divide o primeiro operando pelo segundo. Todos os tipos numéricos têm operadores de divisão predefinidos.  
  
## <a name="remarks"></a>Comentários  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `/` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Uma sobrecarga do operador `/` sobrecarrega implicitamente o [operador /=](division-assignment-operator.md).  
  
 Quando você divide dois números inteiros, o resultado sempre é um número inteiro. Por exemplo, o resultado do 7/3 é 2. Para determinar o resto de 7/3, use o operador de resto ([%](../../../csharp/language-reference/operators/modulus-operator.md)). Para obter um quociente como um número racional ou fração, dê ao dividendo ou divisor o tipo `float` ou o tipo `double`. Você poderá atribuir o tipo implicitamente se expressar o dividendo ou divisor como um decimal colocando um dígito à direita do ponto decimal, como mostra o exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)

