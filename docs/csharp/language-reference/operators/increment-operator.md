---
title: Operador ++ (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: a52f614ce1bbfb8e9d9be686b277c1e69f6f9d35
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44180927"
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

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
