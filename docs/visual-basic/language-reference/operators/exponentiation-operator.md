---
title: ^ Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^
dev_langs:
- VB
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers, rasing
- powers
- arithmetic operators, exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 937d6e4391569f67ccf311c8045415054d6d4f77
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
 O resultado é `number` elevado à potência de `exponent`, sempre que um `Double` valor.  
  
## <a name="supported-types"></a>Tipos com suporte  
 `Double`. Os operandos de qualquer outro tipo são convertidos em `Double`.  
  
## <a name="remarks"></a>Comentários  
 Visual Basic sempre executa exponenciação no [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 O valor de `exponent` pode ser fracionário, negativo, ou ambos.  
  
 Quando mais de uma exponenciação for realizada em uma única expressão, o `^` operador é avaliado como ele é encontrado da esquerda para a direita.  
  
> [!NOTE]
>  O `^` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `^` operador para elevar um número à potência de um expoente. O resultado é o primeiro operando elevado à potência da segunda.  
  
 [!code-vb[20 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 O exemplo anterior produz os seguintes resultados:  
  
 `exp1`é definido como 4 (2 ao quadrado).  
  
 `exp2`é definido como 19683 (3 ao cubo, em seguida, esse valor ao cubo).  
  
 `exp3`é definido como -125 (-5 cúbico).  
  
 `exp4`é definido como 625 (-5 o quarto de energia).  
  
 `exp5`é definido como 2 (raiz cúbica de 8).  
  
 `exp6`é definido como 0,5 (1.0 dividido pela raiz cúbica de 8).  
  
 Observe a importância dos parênteses em expressões no exemplo anterior. Por causa da *precedência do operador*, Visual Basic normalmente executa o `^` operador antes de qualquer outro, mesmo que o operador unário `–` operador. Se `exp4` e `exp6` tinha sido calculados sem parênteses, deve ter produzido os seguintes resultados:  
  
 `exp4 = -5 ^ 4`será calculado como – (5 o quarto de energia), que resultaria em-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0`será calculado como (8 a potência de-1 ou 0,125) dividido por 3.0, o que resultaria em 0.041666666666666666666666666666667.  
  
## <a name="see-also"></a>Consulte também  
 [^ = Operador](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

