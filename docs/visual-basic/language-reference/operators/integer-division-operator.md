---
title: Operador \ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: d1a46f99c21be007d33361ba095a3f0c52fe906c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701142"
---
# <a name="-operator-visual-basic"></a>Operador \ (Visual Basic)
Divide dois números e retorna um resultado inteiro.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Partes  
 `expression1`  
 Necessário. Qualquer expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuante e não assinado e `Decimal`.  
  
## <a name="result"></a>Resultado  
 O resultado é o quociente inteiro de `expression1` dividido por `expression2`, que descarta qualquer resto e retém apenas a parte inteira. Isso é conhecido como *truncamento*.  
  
 O tipo de dados de resultado é um tipo numérico apropriado para os tipos `expression1` de `expression2`dados de e. Consulte as tabelas "aritmética de inteiros" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 O [operador/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, que retém o restante na parte fracionária.  
  
## <a name="remarks"></a>Comentários  
 Antes de executar a divisão, Visual Basic tenta converter qualquer expressão numérica de ponto flutuante em `Long`. Se `Option Strict` for `On`, ocorrerá um erro do compilador. Se `Option Strict` for `Off`, um <xref:System.OverflowException> será possível se o valor estiver fora do intervalo do [tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md). A conversão em `Long` também está sujeita ao *arredondamento do banco*. Para obter mais informações, consulte "partes fracionárias" em [funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Se `expression1` ou`expression2` for avaliado como [Nothing](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
## <a name="attempted-division-by-zero"></a>Tentativa de divisão por zero  
 Se `expression2` for avaliada como zero, o operador `\` lançará uma exceção <xref:System.DivideByZeroException>. Isso é verdadeiro para todos os tipos de dados numéricos dos operandos.  
  
> [!NOTE]
> O operador `\` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `\` para executar divisão de inteiro. O resultado é um inteiro que representa o quociente inteiro dos dois operandos, com o restante Descartado.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 As expressões no exemplo anterior retornam valores de 2, 3, 33 e-22, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Operador \\ =](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Operador/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
