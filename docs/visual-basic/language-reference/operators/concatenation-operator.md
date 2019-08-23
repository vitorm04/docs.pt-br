---
title: '&amp;Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968348"
---
# <a name="amp-operator-visual-basic"></a>&amp;Operador (Visual Basic)
Gera uma concatenação de cadeia de caracteres de duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `String` variável `Object` ou.  
  
 `expression1`  
 Necessário. Qualquer expressão com um tipo de dados que amplia para `String`.  
  
 `expression2`  
 Necessário. Qualquer expressão com um tipo de dados que amplia para `String`.  
  
## <a name="remarks"></a>Comentários  
 Se o tipo de dados `expression1` de `expression2` ou não `String` for, mas se `String`expandir para, ele será `String`convertido em. Se um dos tipos de dados não for ampliado `String`para, o compilador gerará um erro.  
  
 O tipo de dados `result` de `String`é. Se uma ou ambas as expressões forem avaliadas como [Nothing](../../../visual-basic/language-reference/nothing.md) ou se <xref:System.DBNull.Value?displayProperty=nameWithType>tiverem um valor de, elas serão tratadas como uma cadeia de caracteres com um valor de "".  
  
> [!NOTE]
> O `&` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> O caractere de e comercial (&) também pode ser usado para identificar variáveis `Long`como tipo. Para obter mais informações, consulte [tipos de caracteres](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `&` operador para forçar a concatenação de cadeia de caracteres. O resultado é um valor de cadeia de caracteres que representa a concatenação dos dois operandos de cadeia de caracteres.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Operador &=](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores de concatenação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
