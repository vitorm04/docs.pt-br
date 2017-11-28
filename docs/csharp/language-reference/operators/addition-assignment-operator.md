---
title: "Operador += (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91286b3c6b9a7239bcd5d5bac0ef08bfd7fa8345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Operador += (Referência de C#)
Operador de atribuição de adição.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `+=`, como  
  
```  
x += y  
```  
  
 equivale a  
  
```  
x = x + y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O significado do [operador +](../../../csharp/language-reference/operators/addition-operator.md) dependerá dos tipos de `x` e `y` (adição para operandos numéricos, concatenação para operandos de cadeia de caracteres e assim por diante).  
  
 O operador `+=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador +](../../../csharp/language-reference/operators/addition-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
 O operador `+=` também é usado para especificar um método que será chamado em resposta a um evento; esses métodos são chamados de manipuladores de eventos. O uso do operador `+=` nesse contexto é conhecido como *inscrever-se em um evento*. Para obter mais informações, consulte [Como Realizar e Cancelar a Assinatura de Eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md). e [Delegados](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
