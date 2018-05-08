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
ms.openlocfilehash: ef3946e871e1dc248b54932e16f6cae6026da08e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>Operador \ (Visual Basic)
Divide dois números e retorna um resultado inteiro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Partes  
 `expression1`  
 Necessário. Qualquer expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.  
  
## <a name="result"></a>Resultado  
 O resultado é o quociente de inteiro de `expression1` dividido por `expression2`, que descarta qualquer resto e retém apenas a parte inteira. Isso é conhecido como *truncamento*.  
  
 O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte as tabelas de "Aritmética de inteiros" em [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, que retém o resto da parte fracionária.  
  
## <a name="remarks"></a>Comentários  
 Antes de executar a divisão, Visual Basic tenta converter qualquer expressão numérica de ponto flutuante para `Long`. Se `Option Strict` é `On`, ocorre um erro do compilador. Se `Option Strict` é `Off`, uma <xref:System.OverflowException> é possível se o valor está fora do intervalo da [tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md). A conversão em `Long` também está sujeito à *do arredondamento bancário*. Para obter mais informações, veja "Partes fracionários" em [funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Se `expression1` ou `expression2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
## <a name="attempted-division-by-zero"></a>Tentativa de divisão por Zero  
 Se `expression2` for avaliada como zero, o `\` operador gerará um <xref:System.DivideByZeroException> exceção. Isso é verdadeiro para todos os tipos de dados numéricos dos operandos.  
  
> [!NOTE]
>  O `\` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `\` operador para executar uma divisão de inteiro. O resultado é um inteiro que representa o quociente de inteiro dos dois operandos com o resto descartado.  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 As expressões no exemplo anterior retornam valores de 2, 3, 33 e -22, respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [\\= Operador](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [/ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
