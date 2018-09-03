---
title: '&gt;Operador = (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
ms.openlocfilehash: 8749d1dc0670a5a76bda5ee0d69a4a142671c1e6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481756"
---
# <a name="gt-operator-c-reference"></a>&gt;Operador = (Referência de C#)
Todos os tipos numéricos e de enumeração definem um operador relacional "maior ou igual a", `>=`, que retorna `true` se o primeiro operando é maior ou igual ao segundo, `false` caso contrário.  
  
## <a name="remarks"></a>Comentários  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `>=`. Para obter mais informações, consulte [operador](../../../csharp/language-reference/keywords/operator.md). Se `>=` estiver sobrecarregado, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) também deverá estar sobrecarregado. As operações em tipos integrais geralmente são permitidas na enumeração.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
