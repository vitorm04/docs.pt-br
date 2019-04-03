---
title: << Operador (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 75c16c27dc919ba365cbe3c28c61a1e46496b0ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824280"
---
# <a name="-operator-visual-basic"></a>\<\< Operador (Visual Basic)
Executa um deslocamento aritmético à esquerda em um padrão de bit.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Valor numérico integral. O resultado do deslocamento do padrão de bit. O tipo de dados é o mesmo que o de `pattern`.  
  
 `pattern`  
 Necessário. Expressão numérica integral. O padrão de bit a ser deslocado. O tipo de dados deve ser um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).  
  
 `amount`  
 Necessário. Expressão numérica. O número de bits para deslocar o padrão de bit. O tipo de dados deve ser `Integer` ou ampliado para `Integer`.  
  
## <a name="remarks"></a>Comentários  
 Deslocamentos aritméticos não são circulares, que significa que os bits deslocados em uma extremidade do resultado não são reintroduzidos na outra extremidade. Em um deslocamento aritmético à esquerda, os bits deslocados fora do intervalo do tipo de dados de resultado são descartados e as posições de bit vagas à direita serão definidas como zero.  
  
 Para impedir que uma mudança de bits maior do que o resultado pode comportar, Visual Basic mascara o valor de `amount` com uma máscara de tamanho que corresponde ao tipo de dados do `pattern`. O binário AND desses valores é usado para o valor de deslocamento. As máscaras de tamanho são da seguinte maneira:  
  
|Tipo de dados do `pattern`|Máscara de tamanho (decimal)|Máscara de tamanho (hexadecimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Se `amount` for zero, o valor da `result` é idêntico ao valor de `pattern`. Se `amount` é negativo, ele é interpretado como um valor sem sinal e mascarado com a máscara de tamanho apropriado.  
  
 Deslocamentos aritméticos nunca geram exceções de estouro.  
  
> [!NOTE]
>  O `<<` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `<<` operador para executar cálculos aritméticos restante turnos em valores integrais. O resultado sempre tem os mesmos dados de tipo da expressão a ser deslocado.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Os resultados do exemplo anterior são da seguinte maneira:  
  
-   `result1` é 192 (0000 0000 0000 de 1100).  
  
-   `result2` é 3072 (0000 1100 0000 0000).  
  
-   `result3` é de -32768 (1000 0000 0000 0000).  
  
-   `result4` é 384 (0000 0001 1000 0000).  
  
-   `result5` é 0 (deslocadas 15 locais para a esquerda).  
  
 O valor de deslocamento para `result4` é calculado como 17 e 15, que é igual a 1.  
  
## <a name="see-also"></a>Consulte também

- [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operador <<=](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
