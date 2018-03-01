---
title: "?? Operador (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6c2372380d8162d3e7760bba4a43cdb1c568bf5b
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2017
---
# <a name="-operator-c-reference"></a>?? Operador (Referência de C#)
O operador `??` é chamado operador de coalescência nula.  Ele retornará o operando esquerdo se o operando não for nulo; caso contrário, ele retornará o operando direito.  
  
## <a name="remarks"></a>Comentários  
 Um tipo anulável pode representar um valor de domínio do tipo ou o valor pode ser indefinido (nesse caso, o valor será nulo). Você pode usar a expressividade sintática do operador `??` para retornar um valor adequado (o operando direito) quando o operando esquerdo tiver um tipo que permite valor nulo cujo valor seja nulo. Se você tentar atribuir um tipo de valor anulável a um tipo de valor não anulável sem usar o operador `??`, um erro de tempo de compilação será gerado. Se você usar uma conversão e o tipo de valor anulável estiver atualmente indefinido, uma exceção `InvalidOperationException` será acionada.  
  
 Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).  
  
 O resultado de um operador ?? não será considerado constante, mesmo se os dois argumentos forem constantes.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
 [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)  
 [O que exatamente “levantado” significa?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
