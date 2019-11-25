---
title: '>> Operador'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: cabf8c569435cc0fc98282f5e8f5fd410e6708dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347819"
---
# <a name="-operator-visual-basic"></a>>> Operator (Visual Basic)
Performs an arithmetic right shift on a bit pattern.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Integral numeric value. O resultado do deslocamento do padrão de bit. O tipo de dados é o mesmo que o de `pattern`.  
  
 `pattern`  
 Necessário. Expressão numérica integral. O padrão de bit a ser deslocado. O tipo de dados deve ser um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).  
  
 `amount`  
 Necessário. Expressão numérica. O número de bits para deslocar o padrão de bit. O tipo de dados deve ser `Integer` ou ampliado para `Integer`.  
  
## <a name="remarks"></a>Comentários  
 Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end. In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left. This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.  
  
 Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate. If `pattern` is of any unsigned type, the vacated positions are always set to zero.  
  
 To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`. The binary AND of these values is used for the shift amount. The size masks are as follows:  
  
|Data type of `pattern`|Size mask (decimal)|Size mask (hexadecimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 If `amount` is zero, the value of `result` is identical to the value of `pattern`. If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.  
  
 Arithmetic shifts never generate overflow exceptions.  
  
## <a name="overloading"></a>Sobrecarga  
 The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. If your code uses this operator on such a class or structure, be sure you understand its redefined behavior. For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 The following example uses the `>>` operator to perform arithmetic right shifts on integral values. The result always has the same data type as that of the expression being shifted.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 The results of the preceding example are as follows:  
  
- `result1` is 2560 (0000 1010 0000 0000).  
  
- `result2` is 160 (0000 0000 1010 0000).  
  
- `result3` is 2 (0000 0000 0000 0010).  
  
- `result4` is 640 (0000 0010 1000 0000).  
  
- `result5` is 0 (shifted 15 places to the right).  
  
 The shift amount for `result4` is calculated as 18 AND 15, which equals 2.  
  
 The following example shows arithmetic shifts on a negative value.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 The results of the preceding example are as follows:  
  
- `negresult1` is -512 (1111 1110 0000 0000).  
  
- `negresult2` is -1 (the sign bit is propagated).  
  
## <a name="see-also"></a>Consulte também

- [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operador >>=](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
