---
title: Tipos de dados constante e literal (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 1d030f8058cd497212c20bca8f064f2bedc99fce
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389555"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Tipos de dados constante e literal (Visual Basic)
Um literal é um valor que é expresso como em si em vez de um valor de variável ou o resultado de uma expressão, como o número 3 ou a cadeia de caracteres "Hello". Uma constante é um nome significativo que toma o lugar de um literal e mantém esse mesmo valor em todo o programa, em vez de uma variável, cujo valor pode ser alterado.  
  
 Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar todas as constantes explicitamente com um tipo de dados. No exemplo a seguir, o tipo de dados `MyByte` for declarado explicitamente como tipo de dados `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Quando `Option Infer` está `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula. O compilador determina o tipo da constante do tipo da expressão. Um numérico literal de inteiro é convertido por padrão para o `Integer` tipo de dados. Tipo de dados padrão para são de números de ponto flutuante `Double`e as palavras-chave `True` e `False` especificar um `Boolean` constante.  
  
## <a name="literals-and-type-coercion"></a>Literais e coerção de tipo  
 Em alguns casos, talvez você queira forçar um literal para um determinado tipo de dados; Por exemplo, ao atribuir um valor literal inteiro muito grande para uma variável do tipo `Decimal`. O exemplo a seguir produz um erro:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Os resultados de erro da representação do literal. O `Decimal` tipo de dados pode conter um valor muito grande, mas o literal implicitamente é representado como um `Long`, que não é possível.  
  
 Você pode forçar um literal para um determinado tipo de dados de duas maneiras: anexando um caractere de tipo a ele, ou colocando-o entre caracteres delimitadores. Um caractere de tipo ou delimitador caracteres deve imediatamente preceder e/ou siga o literal, sem nenhum espaço intermediário ou caracteres de qualquer tipo.  
  
 Para fazer com que o exemplo anterior funcione, você pode acrescentar a `D` digite o caractere literal, o que faz com que ele seja representado como um `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 O exemplo a seguir demonstra o uso correto de caracteres de tipo e caracteres de delimitadores:  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 A tabela a seguir mostra os caracteres delimitadores e tipos de caracteres disponíveis no Visual Basic.  
  
|Tipo de dados|Caractere delimitador|Caractere de tipo acrescentado|  
|---|---|---|  
|`Boolean`|(nenhum)|(nenhum)|  
|`Byte`|(nenhum)|(nenhum)|  
|`Char`|"|C|  
|`Date`|#|(nenhum)|  
|`Decimal`|(nenhum)|1!d ou @|  
|`Double`|(nenhum)|R ou #|  
|`Integer`|(nenhum)|I ou %|  
|`Long`|(nenhum)|L ou &|  
|`Short`|(nenhum)|S|  
|`Single`|(nenhum)|F ou!|  
|`String`|"|(nenhum)|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes Definidas pelo Usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [Como declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [Visão Geral de Constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Instrução Option Explicit](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Visão geral de Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)  
 [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
