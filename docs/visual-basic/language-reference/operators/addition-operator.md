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
ms.openlocfilehash: 3187551afb7d25470f48dad894188766a811bb0a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701005"
---
# <a name="-operator-visual-basic"></a>Operador + (Visual Basic)
Adiciona dois números ou retorna o valor positivo de uma expressão numérica. Também pode ser usado para concatenar duas expressões de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb
expression1 + expression2
```
  
ou

```vb  
+expression1  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression1`|Necessário. Qualquer expressão numérica ou de cadeia de caracteres.|  
|`expression2`|Necessário, a `+` menos que o operador esteja calculando um valor negativo. Qualquer expressão numérica ou de cadeia de caracteres.|  
  
## <a name="result"></a>Resultado  
 Se `expression1` e`expression2` forem ambos numéricos, o resultado será sua soma aritmética.  
  
 Se `expression2` estiver ausente, o operador `+` será o operador de identidade *unário* para o valor inalterado de uma expressão. Nesse sentido, a operação consiste em reter o sinal de `expression1`, portanto, o resultado será negativo se `expression1` for negativo.  
  
 Se `expression1` e`expression2` forem as duas cadeias de caracteres, o resultado será a concatenação de seus valores.  
  
 Se `expression1` e `expression2` forem de tipos mistos, a ação executada dependerá de seus tipos, do conteúdo e da configuração da [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Para obter mais informações, consulte as tabelas em "Comentários".  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuante e não assinado `Decimal`e `String`e.  
  
## <a name="remarks"></a>Comentários  
 Em geral, `+` o executa a adição aritmética quando possível e concatena somente quando ambas as expressões são cadeias de caracteres.  
  
 Se nenhuma expressão for uma `Object`, Visual Basic executará as seguintes ações.  
  
|Tipos de dados de expressões|Ação por compilador|  
|---|---|  
|As duas expressões são tipos de dados`SByte`numéricos `Short`( `UShort`, `Integer` `UInteger` `Decimal` `Single` ,,`Double`,,,, ,,ou)`ULong` `Byte` `Long`|Agrega. O tipo de dados de resultado é um tipo numérico apropriado para os tipos `expression1` de `expression2`dados de e. Consulte as tabelas "aritmética de inteiros" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Ambas as expressões são do tipo`String`|Concatenar.|  
|Uma expressão é um tipo de dados numérico e a outra é uma cadeia de caracteres|Se `Option Strict` for`On`, gere um erro do compilador.<br /><br /> Se `Option Strict` `String` `Double` for `Off`, converta implicitamente o para e adicione.<br /><br /> Se o `String` não puder ser convertido `Double`em, lance uma <xref:System.InvalidCastException> exceção.|  
|Uma expressão é um tipo de dados numérico e a outra é [Nothing](../../../visual-basic/language-reference/nothing.md)|Adicionar, com `Nothing` valor igual a zero.|  
|Uma expressão é uma cadeia de caracteres e a outra é`Nothing`|Concatenar, com `Nothing` valor como "".|  
  
 Se uma expressão for uma `Object` expressão, Visual Basic executará as seguintes ações.  
  
|Tipos de dados de expressões|Ação por compilador|  
|---|---|  
|`Object`a expressão contém um valor numérico e o outro é um tipo de dados numérico|Se `Option Strict` for`On`, gere um erro do compilador.<br /><br /> Se `Option Strict` for`Off`, adicione.|  
|`Object`a expressão contém um valor numérico e o outro é do tipo`String`|Se `Option Strict` for`On`, gere um erro do compilador.<br /><br /> Se `Option Strict` `String` `Double` for `Off`, converta implicitamente o para e adicione.<br /><br /> Se o `String` não puder ser convertido `Double`em, lance uma <xref:System.InvalidCastException> exceção.|  
|`Object`a expressão contém uma cadeia de caracteres e a outra é um tipo de dados numérico|Se `Option Strict` for`On`, gere um erro do compilador.<br /><br /> Se `Option Strict` `Object` `Double` for `Off`, converta implicitamente a cadeia de caracteres para e adicione.<br /><br /> Se a cadeia `Object` de caracteres não puder `Double`ser convertida em <xref:System.InvalidCastException> , lance uma exceção.|  
|`Object`a expressão contém uma cadeia de caracteres e a outra é do tipo`String`|Se `Option Strict` for`On`, gere um erro do compilador.<br /><br /> Se `Option Strict` `Object` for `Off` ,`String` então converta implicitamente e concatene.|  
  
 Se ambas as expressões `Object` forem expressões, Visual Basic executará as seguintes`Option Strict Off` ações (somente).  
  
|Tipos de dados de expressões|Ação por compilador|  
|---|---|  
|Ambas `Object` as expressões contêm valores numéricos|Agrega.|  
|Ambas `Object` as expressões são do tipo`String`|Concatenar.|  
|Uma `Object` expressão contém um valor numérico e a outra contém uma cadeia de caracteres|Converta implicitamente a `Object` cadeia `Double` de caracteres para e adicione.<br /><br /> Se a cadeia `Object` de caracteres não puder ser convertida em um valor numérico <xref:System.InvalidCastException> , lance uma exceção.|  
  
 Se qualquer expressão `Object` for avaliada como [Nothing](../../../visual-basic/language-reference/nothing.md) ou <xref:System.DBNull>, o operador `+` a tratará como um `String` com um valor de "".  
  
> [!NOTE]
> Ao usar o operador `+` , talvez você não consiga determinar se a adição ou a concatenação de cadeia de caracteres ocorrerá. Use o `&` operador para concatenação para eliminar ambigüidade e fornecer código de autodocumentação.  
  
## <a name="overloading"></a>Sobrecarga  
 O operador `+` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `+` o operador para adicionar números. Se os operandos forem numéricos, Visual Basic calculará o resultado aritmético. O resultado aritmético representa a soma dos dois operandos.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Você também pode usar o `+` operador para concatenar cadeias de caracteres. Se os operandos forem as duas cadeias de caracteres, Visual Basic as concatena. O resultado da concatenação representa uma única cadeia de caracteres que consiste no conteúdo dos dois operandos um após o outro.  
  
 Se os operandos forem de tipos mistos, o resultado dependerá da configuração da [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). O exemplo a seguir ilustra o resultado `Option Strict` quando `On`é.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 O exemplo a seguir ilustra o resultado `Option Strict` quando `Off`é.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Para eliminar a ambiguidade, você deve usar o `&` operador em vez `+` de para concatenação.  
  
## <a name="see-also"></a>Consulte também

- [Operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
