---
title: ?? Operador – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 153accdc4995065563b00da0fd62992341c06cf1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241873"
---
# <a name="-operator-c-reference"></a>?? Operador (Referência de C#)
O operador `??` é chamado operador de coalescência nula.  Ele retornará o operando esquerdo se o operando não for nulo; caso contrário, ele retornará o operando direito.  
  
## <a name="remarks"></a>Comentários  
 Um tipo anulável pode representar um valor de domínio do tipo ou o valor pode ser indefinido (nesse caso, o valor será nulo). Você pode usar a expressividade sintática do operador `??` para retornar um valor adequado (o operando direito) quando o operando esquerdo tiver um tipo que permite valor nulo cujo valor seja nulo. Se você tentar atribuir um tipo de valor anulável a um tipo de valor não anulável sem usar o operador `??`, um erro de tempo de compilação será gerado. Se você usar uma conversão e o tipo de valor anulável estiver atualmente indefinido, uma exceção `InvalidOperationException` será acionada.  
  
 Para obter mais informações, consulte [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md).  
  
 O resultado de um operador ?? não será considerado constante, mesmo se os dois argumentos forem constantes.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  

Para obter mais informações, veja [O operador coalescente nulo](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) na [Especificação da Linguagem C#](../language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
- [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)  
- [O que exatamente “levantado” significa?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
