---
title: Operador ^ (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>Operador ^ (Visual Basic)
Eleva um número à potência de outro número.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>Partes  
 `number`  
 Necessário. Qualquer expressão numérica.  
  
 `exponent`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="result"></a>Resultado  
 O resultado é `number` elevado à potência de `exponent`, sempre como um `Double` valor.  
  
## <a name="supported-types"></a>Tipos com suporte  
 `Double`. Operandos de qualquer outro tipo são convertidos em `Double`.  
  
## <a name="remarks"></a>Comentários  
 Visual Basic sempre executa exponenciação no [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 O valor de `exponent` pode ser fracionário, negativo, ou ambos.  
  
 Quando mais de um expoente é executada em uma única expressão, o `^` operador é avaliado como ele é encontrado da esquerda para a direita.  
  
> [!NOTE]
>  O `^` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `^` operador para elevar um número à potência de um expoente. O resultado é o primeiro operando elevado à potência da segunda.  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 O exemplo anterior gera os seguintes resultados:  
  
 `exp1`é definido como 4 (2 quadrado).  
  
 `exp2`é definido como 19683 (3 ao cubo, em seguida, esse valor cúbico).  
  
 `exp3`é definido como -125 (-5 cúbico).  
  
 `exp4`é definido como 625 (-5 para o quarto power).  
  
 `exp5`é definido como 2 (raiz cúbica de 8).  
  
 `exp6`é definido como 0,5 (1.0 dividido pela raiz cúbica de 8).  
  
 Observe a importância de parênteses nas expressões no exemplo anterior. Porque *precedência do operador*, Visual Basic normalmente executa o `^` operador antes de quaisquer outros, até mesmo o operador unário `–` operador. Se `exp4` e `exp6` tinha sido calculada sem parênteses, deve ter produzido os seguintes resultados:  
  
 `exp4 = -5 ^ 4`será calculado como – (5 para o quarto power), que pode resultar em-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0`será calculado como (8 para a potência de-1 ou 0,125) dividido pelo 3.0, o que resultaria em 0.041666666666666666666666666666667.  
  
## <a name="see-also"></a>Consulte também  
 [Operador ^=](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
