---
title: Operador *= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: f8604cdadeda14a5761bc923bd966186fd258a6d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245344"
---
# <a name="-operator-c-reference"></a>Operador *= (Referência de C#)
O operador de atribuição de multiplicação binária.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `*=`, como  
  
```csharp  
x *= y  
```  
  
 equivale a  
  
```csharp  
x = x * y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [* operador](../../../csharp/language-reference/operators/multiplication-operator.md) é predefinido para que os tipos numéricos executem multiplicação.  
  
 O operador `*=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador *](../../../csharp/language-reference/operators/multiplication-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
