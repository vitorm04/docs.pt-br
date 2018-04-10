---
title: Operador ++ (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
