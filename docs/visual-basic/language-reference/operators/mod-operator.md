---
title: Operador Mod (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Mod
dev_langs:
- VB
helpviewer_keywords:
- remainder (Mod operator)
- division operator, Mod operator
- modulus operator, Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators, Mod
- math operators
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d37a60b6d8fb9aa6d76a246d18e7bf0d5d985d36
ms.lasthandoff: 03/13/2017

---
# <a name="mod-operator-visual-basic"></a>Operador Mod (Visual Basic)
Divide dois números e retorna somente o resto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
number1 Mod number2  
```  
  
## <a name="parts"></a>Partes  
 `number1`  
 Necessário. Qualquer expressão numérica.  
  
 `number2`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos. Isso inclui os tipos de ponto flutuantes e não assinados e `Decimal`.  
  
## <a name="result"></a>Resultado  
 O resultado é o que resta após `number1` é dividida por `number2`. Por exemplo, a expressão `14 Mod 4` for avaliada como 2.  
  
## <a name="remarks"></a>Comentários  
 Se qualquer um dos `number1` ou `number2` é um valor de ponto flutuante, o restante da divisão de ponto flutuante é retornado. O tipo de dados do resultado é o menor tipo de dados que pode conter todos os possíveis valores resultantes de divisão com os tipos de dados de `number1` e `number2`.  
  
 Se `number1` ou `number2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
 Relacionadas operadores incluem o seguinte:  
  
-   O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro de uma divisão. Por exemplo, a expressão `14 \ 4` for avaliada como 3.  
  
-   O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, incluindo o restante, como um número de ponto flutuante. Por exemplo, a expressão `14 / 4` avaliará como 3.5.  
  
## <a name="attempted-division-by-zero"></a>Tentativa de divisão por Zero  
 Se `number2` for avaliada como zero, o comportamento do `Mod` operador depende do tipo de dados dos operandos. Uma divisão integral gera uma <xref:System.DivideByZeroException>exceção.</xref:System.DivideByZeroException> <xref:System.Double.NaN>.</xref:System.Double.NaN> Retorna de uma divisão de ponto flutuante  
  
## <a name="equivalent-formula"></a>Fórmula equivalente  
 A expressão `a Mod b` é equivalente a uma das fórmulas a seguir:  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>Ponto flutuante imprecisão  
 Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória. Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador. Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `Mod` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento. Se seu código se aplica `Mod` para uma instância de uma classe ou estrutura que inclua tal uma sobrecarga, certifique-se que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Mod` operador para dividir dois números e retornar somente o resto. Se o número for um número de ponto flutuante, o resultado é um número de ponto flutuante que representa o restante.  
  
 [!code-vb[VbVbalrOperators&#31;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra a imprecisão potencial de operandos de ponto flutuantes. Na primeira instrução, os operandos são `Double`, e 0.2 é uma fração binária infinitamente de repetição com um valor armazenado de 0.20000000000000001. Tipo de caractere na segunda instrução, o literal `D` força ambos os operandos para `Decimal`, e 0.2 tem uma representação exata.  
  
 [!code-vb[32 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A></xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A></xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [\ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
