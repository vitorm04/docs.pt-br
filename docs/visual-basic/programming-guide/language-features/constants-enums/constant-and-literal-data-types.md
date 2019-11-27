---
title: Tipos de dados constante e literal
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 8ebecddfab0724023c269e92c1fc5534f096bf1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333724"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Tipos de dados constante e literal (Visual Basic)
Um literal é um valor que é expresso como ele mesmo, e não como o valor de uma variável ou o resultado de uma expressão, como o número 3 ou a cadeia de caracteres "Olá". Uma constante é um nome significativo que assume o lugar de um literal e retém esse mesmo valor em todo o programa, em oposição a uma variável, cujo valor pode ser alterado.  
  
 Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar todas as constantes explicitamente com um tipo de dados. No exemplo a seguir, o tipo de dados de `MyByte` é declarado explicitamente como tipo de dados `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 Quando `Option Infer` é `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com uma cláusula `As`. O compilador determina o tipo da constante do tipo da expressão. Um literal inteiro numérico é convertido por padrão no tipo de dados `Integer`. O tipo de dados padrão para números de ponto flutuante é `Double`e as palavras-chave `True` e `False` especificam uma constante de `Boolean`.  
  
## <a name="literals-and-type-coercion"></a>Literais e coerção de tipo  
 Em alguns casos, talvez você queira forçar um literal para um tipo de dados específico; por exemplo, ao atribuir um valor literal integral especialmente grande a uma variável do tipo `Decimal`. O exemplo a seguir produz um erro:  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 O erro resulta da representação do literal. O tipo de dados `Decimal` pode conter um valor tão grande, mas o literal é representado implicitamente como um `Long`, que não pode.  
  
 Você pode forçar um literal para um tipo de dados específico de duas maneiras: anexando um caractere de tipo a ele ou colocando-o entre caracteres delimitadores. Um caractere de tipo ou caracteres delimitadores devem anteceder e/ou seguir o literal imediatamente, sem nenhum espaço intermediário ou caracteres de qualquer tipo.  
  
 Para que o exemplo anterior funcione, você pode acrescentar o caractere do tipo `D` ao literal, o que faz com que ele seja representado como um `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 O exemplo a seguir demonstra o uso correto de caracteres de tipo e caracteres de delimitador:  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 A tabela a seguir mostra os caracteres delimitadores e os caracteres de tipo disponíveis no Visual Basic.  
  
|Tipo de dados|Caractere delimitador|Caractere de tipo acrescentado|  
|---|---|---|  
|`Boolean`|(nenhum)|(nenhum)|  
|`Byte`|(nenhum)|(nenhum)|  
|`Char`|"|C|  
|`Date`|#|(nenhum)|  
|`Decimal`|(nenhum)|D ou @|  
|`Double`|(nenhum)|R ou #|  
|`Integer`|(nenhum)|I ou%|  
|`Long`|(nenhum)|L ou &|  
|`Short`|(nenhum)|S|  
|`Single`|(nenhum)|F ou!|  
|`String`|"|(nenhum)|  
  
## <a name="see-also"></a>Consulte também

- [Constantes Definidas pelo Usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [Como declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [Visão Geral de Constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Instrução Option Explicit](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Visão geral de Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
