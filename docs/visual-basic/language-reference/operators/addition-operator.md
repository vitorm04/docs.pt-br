---
title: + Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+
dev_langs:
- VB
helpviewer_keywords:
- arithmetic operators, addition
- + operator
- concatenation operators, syntax
- strings [Visual Basic], concatenating
- sum operator
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
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
ms.openlocfilehash: fc247ef2ed1073cae2a78e2d2bc2d40d59adeccb
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>Operador + (Visual Basic)
Adiciona dois números ou retorna o valor positivo de uma expressão numérica. Também pode ser usado para concatenar duas expressões de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
 Se `expression2` estiver ausente, o `+` operador é a *unário* operador de identidade para o valor inalterado de uma expressão. Nesse sentido, a operação consiste em manter o sinal de `expression1`, portanto, o resultado é negativo se `expression1` for negativo.  
  
 Se `expression1` e `expression2` são as duas cadeias de caracteres, o resultado é a concatenação de seus valores.  
  
 Se `expression1` e `expression2` são de tipos mistos, a ação tomada depende seus tipos, seu conteúdo e a configuração do [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Para obter mais informações, consulte as tabelas em "Comentários".  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`, e `String`.  
  
## <a name="remarks"></a>Comentários  
 Em geral, `+` executa adição aritmética quando possível e concatena somente quando as duas expressões são cadeias de caracteres.  
  
 Se nenhuma expressão for um `Object`, Visual Basic toma as seguintes medidas.  
  
|Tipos de dados de expressões|Ação pelo compilador|  
|---|---|  
|Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)|Adicione. O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte as tabelas de "Aritmética de inteiros" em [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Ambas as expressões forem do tipo`String`|Concatene.|  
|Uma expressão é um tipo de dados numéricos e a outra é uma cadeia de caracteres|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, em seguida, converter implicitamente o `String` para `Double` e adicionar.<br /><br /> Se o `String` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException>|  
|Uma expressão é um tipo de dados numéricos e a outra é [nada](../../../visual-basic/language-reference/nothing.md)|Adicionar, com `Nothing` com valor igual a zero.|  
|Uma expressão é uma cadeia de caracteres e a outra é`Nothing`|Concatenar com `Nothing` valores como "".|  
  
 Se uma expressão for um `Object` expressão, Visual Basic toma as seguintes medidas.  
  
|Tipos de dados de expressões|Ação pelo compilador|  
|---|---|  
|`Object`a expressão contém um valor numérico e a outra é um tipo de dados numéricos|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, em seguida, adicione.|  
|`Object`a expressão contém um valor numérico e a outra é do tipo`String`|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, em seguida, converter implicitamente o `String` para `Double` e adicionar.<br /><br /> Se o `String` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException>|  
|`Object`a expressão contém uma cadeia de caracteres e a outra é um tipo de dados numéricos|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, em seguida, converter implicitamente a cadeia de caracteres `Object` para `Double` e adicionar.<br /><br /> Se a cadeia de caracteres `Object` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException>|  
|`Object`a expressão contém uma cadeia de caracteres e a outra é do tipo`String`|Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, em seguida, converter implicitamente `Object` para `String` e concatenar.|  
  
 Se ambas as expressões forem `Object` expressões, Visual Basic toma as seguintes medidas (`Option Strict Off` somente).  
  
|Tipos de dados de expressões|Ação pelo compilador|  
|---|---|  
|Ambos `Object` expressões contém valores numéricos|Adicione.|  
|Ambos `Object` expressões forem do tipo`String`|Concatene.|  
|Um `Object` expressão contém um valor numérico e a outra contém uma cadeia de caracteres|Converter implicitamente a cadeia de caracteres `Object` para `Double` e adicionar.<br /><br /> Se a cadeia de caracteres `Object` não pode ser convertido em um valor numérico, em seguida, gere um <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException>|  
  
 Se qualquer um dos `Object` expressão é avaliada como [nada](../../../visual-basic/language-reference/nothing.md) ou <xref:System.DBNull>, o `+` operador tratá-la como um `String` com um valor de "".</xref:System.DBNull>  
  
> [!NOTE]
>  Quando você usa o `+` operador, você não poderá determinar se a concatenação de cadeia de caracteres ou adição ocorrerá. Use o `&` operador de concatenação para eliminar ambiguidade e fornecer código de documentação própria.  
  
## <a name="overloading"></a>Sobrecarga  
 O `+` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `+` para adicionar números. Se os operandos forem numéricos, o Visual Basic calcula o resultado aritmético. O resultado aritmético representa a soma de dois operandos.  
  
 [!code-vb[VbVbalrOperators n º&6;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 Você também pode usar o `+` operador concatenar cadeias de caracteres. Se os operandos forem ambos cadeias de caracteres, o Visual Basic os concatena. O resultado da concatenação representa uma única cadeia de caracteres consistindo no conteúdo de dois operandos um após o outro.  
  
 Se os operandos forem de tipos mistos, o resultado depende da configuração do [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). O exemplo a seguir ilustra o resultado quando `Option Strict` é `On`.  
  
 [!code-vb[VbVbalrOperators&#53;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators&#50;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators&#51;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 O exemplo a seguir ilustra o resultado quando `Option Strict` é `Off`.  
  
 [!code-vb[VbVbalrOperators&#54;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators&#50;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators&#52;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 Para eliminar a ambiguidade, você deve usar o `&` em vez do operador `+` para concatenação.  
  
## <a name="see-also"></a>Consulte também  
 [< / Operador](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [Operadores de concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)

