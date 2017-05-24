---
title: '- Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Negate
- vb.-
dev_langs:
- VB
helpviewer_keywords:
- '- operator [Visual Basic]'
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator
- operators [Visual Basic], arithmetic
- subtraction operator, syntax
- arithmetic operators, subtraction
- difference operator
- math operators
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
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
ms.openlocfilehash: 7f45094da7bc61687d9c767d25858aa214bf1978
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
 O resultado é a diferença entre `expression1` e `expression2`, ou o valor negado do `expression1`.  
  
 O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte as tabelas de "Aritmética de inteiros" em [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos. Isso inclui os tipos de ponto flutuantes e não assinados e `Decimal`.  
  
## <a name="remarks"></a>Comentários  
 No primeiro uso mostrado a sintaxe mostrada anteriormente, o `–` operador é a *binário* operador de subtração aritmético para a diferença entre duas expressões numéricas.  
  
 No segundo uso mostrado a sintaxe mostrada anteriormente, o `–` operador é a *unário* operador de negação para o valor negativo de uma expressão. Nesse sentido, a negação consiste em Reverter o sinal do `expression1` para que o resultado será positivo se `expression1` for negativo.  
  
 Se qualquer expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), o `–` operador tratá-la como zero.  
  
> [!NOTE]
>  O `–` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `–` operador para calcular e retornar a diferença entre dois números e para negar um número.  
  
 [!code-vb[VbVbalrOperators n º&10;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 Após a execução dessas instruções `binaryResult` contém 124.45 e `unaryResult` contém –334.90.  
  
## <a name="see-also"></a>Consulte também  
 [-= Operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

