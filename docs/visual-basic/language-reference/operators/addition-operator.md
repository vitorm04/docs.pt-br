---
title: + Operador (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 91806c204c313956b292eb9c9be078991f733b4e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420896"
---
# <a name="-operator-visual-basic"></a>Operador + (Visual Basic)
Adiciona dois números ou retorna o valor positivo de uma expressão numérica. Também pode ser usado para concatenar duas expressões de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression1`|Necessário. Qualquer expressão numérica ou de cadeia de caracteres.|  
|`expression2`|Necessário a menos que o `+` operador está calculando um valor negativo. Qualquer expressão numérica ou de cadeia de caracteres.|  
  
## <a name="result"></a>Resultado  
 Se `expression1` e `expression2` forem numéricos, o resultado é sua soma aritmética.  
  
 Se `expression2` estiver ausente, o `+` operador é a *unário* operador de identidade para o valor inalterado de uma expressão. Nesse sentido, a operação consiste em manter o sinal de `expression1`, portanto, o resultado será negativo se `expression1` é negativo.  
  
 Se `expression1` e `expression2` são ambas as cadeias de caracteres, o resultado é a concatenação de seus valores.  
  
 Se `expression1` e `expression2` são de tipos mistos, a ação tomada depende de seus tipos, seu conteúdo e a configuração das [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Para obter mais informações, consulte as tabelas em "Comentários".  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`, e `String`.  
  
## <a name="remarks"></a>Comentários  
 Em geral, `+` executa aritmética de adição quando possível e concatena somente quando as duas expressões são cadeias de caracteres.  
  
 Se nenhuma expressão for um `Object`, Visual Basic toma as seguintes ações.  
  
|Tipos de dados de expressões|Ação pelo compilador|  
|---|---|  
|Ambas as expressões forem de tipos de dados numéricos (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ou `Double`)|Adicione. O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte as tabelas "Aritmética de inteiros" [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Ambas as expressões forem do tipo `String`|Concatene.|  
|Uma expressão é um tipo de dados numéricos e a outra é uma cadeia de caracteres|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` está `Off`, em seguida, converter implicitamente o `String` para `Double` e adicione.<br /><br /> Se o `String` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException> exceção.|  
|Uma expressão é um tipo de dados numéricos e a outra é [nada](../../../visual-basic/language-reference/nothing.md)|Adicionar, com `Nothing` com o valor como zero.|  
|Uma expressão é uma cadeia de caracteres, e o outro é `Nothing`|Concatenar com `Nothing` com valores como "".|  
  
 Se uma expressão for um `Object` expressão, o Visual Basic usa as seguintes ações.  
  
|Tipos de dados de expressões|Ação pelo compilador|  
|---|---|  
|`Object` a expressão contém um valor numérico e a outra é um tipo de dados numéricos|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, em seguida, adicione.|  
|`Object` a expressão contém um valor numérico e a outra é do tipo `String`|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` está `Off`, em seguida, converter implicitamente o `String` para `Double` e adicione.<br /><br /> Se o `String` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException> exceção.|  
|`Object` a expressão contém uma cadeia de caracteres e o outro é um tipo de dados numéricos|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` está `Off`, em seguida, converter implicitamente a cadeia de caracteres `Object` para `Double` e adicione.<br /><br /> Se a cadeia de caracteres `Object` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException> exceção.|  
|`Object` a expressão contém uma cadeia de caracteres e a outra é do tipo `String`|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` está `Off`, em seguida, converter implicitamente `Object` para `String` e concatená-los.|  
  
 Se ambas as expressões forem `Object` expressões, o Visual Basic usa as seguintes ações (`Option Strict Off` somente).  
  
|Tipos de dados de expressões|Ação pelo compilador|  
|---|---|  
|Ambos `Object` expressões contêm valores numéricos|Adicione.|  
|Ambos `Object` expressões forem do tipo `String`|Concatene.|  
|Um `Object` expressão contém um valor numérico e o outro contém uma cadeia de caracteres|Converter implicitamente a cadeia de caracteres `Object` para `Double` e adicione.<br /><br /> Se a cadeia de caracteres `Object` não pode ser convertido em um valor numérico, em seguida, gere um <xref:System.InvalidCastException> exceção.|  
  
 Se qualquer um dos `Object` expressão é avaliada como [nada](../../../visual-basic/language-reference/nothing.md) ou <xref:System.DBNull>, o `+` operador tratará como um `String` com um valor de "".  
  
> [!NOTE]
>  Quando você usa o `+` operador, você não pode ser capaz de determinar se a adição ou a cadeia de caracteres de concatenação ocorrerá. Use o `&` operador de concatenação para eliminar a ambiguidade e fornecer o código autodocumentado.  
  
## <a name="overloading"></a>Sobrecarga  
 O `+` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `+` operador para adicionar números. Se os operandos forem numéricos, o Visual Basic calcula o resultado de aritmético. O resultado aritmético representa a soma dos dois operandos.  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 Você também pode usar o `+` operador concatenar cadeias de caracteres. Se os operandos forem ambas as cadeias de caracteres, o Visual Basic os concatena. O resultado da concatenação representa uma única cadeia de caracteres consistindo no conteúdo de dois operandos um após o outro.  
  
 Se os operandos forem de tipos mistos, o resultado depende da configuração das [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). O exemplo a seguir ilustra o resultado quando `Option Strict` é `On`.  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 O exemplo a seguir ilustra o resultado quando `Option Strict` é `Off`.  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 Para eliminar a ambiguidade, você deve usar o `&` em vez do operador `+` para concatenação.  
  
## <a name="see-also"></a>Consulte também  
 [Operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
