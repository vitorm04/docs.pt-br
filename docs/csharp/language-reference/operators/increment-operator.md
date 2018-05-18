---
title: Operador ++ (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: 0fe1150ca7267d02feeab33168eab7f79734c2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>Operador ++ (Referência de C#)
O operador de incremento (`++`) incrementa seu operando em 1. O operador de incremento pode ser exibido antes ou depois de seu operando: `++variable` e `variable++`.  
  
## <a name="remarks"></a>Comentários  
 A primeira forma é uma operação de incremento de prefixo. O resultado da operação será o valor do operando "depois" que ele for incrementado.  
  
 A segunda forma é uma operação de incremento pós-fixada. O resultado da operação será o valor do operando antes de ser incrementado.  
  
 Tipos numéricos e de enumeração têm operadores de incremento predefinidos. Os tipos definidos pelo usuário podem sobrecarregar o operador `++`. As operações em tipos integrais geralmente são permitidas na enumeração.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
