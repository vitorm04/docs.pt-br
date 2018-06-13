---
title: '- Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 4df8eb3844ed20fd24ca375f77cea46b9c6cee37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604309"
---
# <a name="--operator-visual-basic"></a>Operador - (Visual Basic)
Retorna a diferença entre duas expressões numéricas ou o valor negativo de uma expressão numérica.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>Partes  
 `expression1`  
 Necessário. Qualquer expressão numérica.  
  
 `expression2`  
 Necessário a menos que o `–` operador está calculando um valor negativo. Qualquer expressão numérica.  
  
## <a name="result"></a>Resultado  
 O resultado é a diferença entre `expression1` e `expression2`, ou o valor negado da `expression1`.  
  
 O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte as tabelas de "Aritmética de inteiros" em [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos. Isso inclui os tipos de ponto flutuantes e não assinados e `Decimal`.  
  
## <a name="remarks"></a>Comentários  
 No primeiro uso mostrado a sintaxe mostrada anteriormente, o `–` operador é a *binário* operador de subtração aritmético para a diferença entre duas expressões numéricas.  
  
 No segundo uso mostrado a sintaxe mostrada anteriormente, o `–` operador é a *unário* operador de negação para o valor negativo de uma expressão. Nesse sentido, a negação consiste em Reverter o sinal do `expression1` para que o resultado é positivo se `expression1` for negativo.  
  
 Se qualquer expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), o `–` operador trata como zero.  
  
> [!NOTE]
>  O `–` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `–` operador para calcular e retornar a diferença entre dois números e, em seguida, para negar um número.  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 Após a execução dessas instruções `binaryResult` contém 124.45 e `unaryResult` contém –334.90.  
  
## <a name="see-also"></a>Consulte também  
 [-= Operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
