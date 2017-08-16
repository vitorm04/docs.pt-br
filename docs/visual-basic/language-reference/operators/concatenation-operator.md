---
title: '&amp;Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&
dev_langs:
- VB
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators, syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: 12
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
ms.openlocfilehash: 4123b7d36f18cc57140e7c36fbac6ff5e71a6cc5
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="amp-operator-visual-basic"></a>&amp;Operador (Visual Basic)
Gera uma concatenação de cadeia de caracteres de duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `String` ou `Object` variável.  
  
 `expression1`  
 Necessário. Qualquer expressão com um tipo de dados que amplia a `String`.  
  
 `expression2`  
 Necessário. Qualquer expressão com um tipo de dados que amplia a `String`.  
  
## <a name="remarks"></a>Comentários  
 Se o tipo de dados `expression1` ou `expression2` não é `String` mas amplia a `String`, ele é convertido em `String`. Se qualquer um dos tipos de dados não se estendem ao `String`, o compilador gerará um erro.  
  
 O tipo de dados `result` é `String`. Se uma ou ambas as expressões forem avaliados como [nada](../../../visual-basic/language-reference/nothing.md) ou tem um valor de <xref:System.DBNull.Value?displayProperty=fullName>, eles são tratados como uma cadeia de caracteres com um valor de "".</xref:System.DBNull.Value?displayProperty=fullName>  
  
> [!NOTE]
>  O `&` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
>  O caractere e comercial (&) também pode ser usado para identificar variáveis como tipo `Long`. Para obter mais informações, consulte [caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `&` operador para forçar a concatenação de cadeia de caracteres. O resultado é um valor de cadeia de caracteres que representa a concatenação dos operandos de cadeia de caracteres de dois.  
  
 [!code-vb[VbVbalrOperators n º&2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [< / Operador =](../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [Operadores de concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores de concatenação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)

