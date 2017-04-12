---
title: Tipos de dados constante e Literal (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring constants, literal data types
- data types [Visual Basic], declaring
- constants, declaring
- explicit declarations
- literals, coercing data type
- declarations, data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 22ad31415ab560b7fd0180a6dadd6d2dcd7ec77a
ms.lasthandoff: 03/13/2017

---
# <a name="constant-and-literal-data-types-visual-basic"></a>Tipos de dados constante e literal (Visual Basic)
Um literal é um valor que é expresso como si mesmo em vez de um valor de variável ou o resultado de uma expressão, como o número 3 ou a cadeia de caracteres "Hello". Uma constante é um nome significativo que toma o lugar de um literal e mantém esse mesmo valor em todo o programa, em vez de uma variável, cujo valor pode ser alterado.  
  
 Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar todas as constantes explicitamente com um tipo de dados. No exemplo a seguir, o tipo de dados `MyByte` for declarado explicitamente como tipo de dados `Byte`:  
  
 [!code-vb[VbVbalrConstants n º&1;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Quando `Option Infer` é `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula. O compilador determina o tipo da constante do tipo da expressão. Um literal numérico de inteiro é convertido por padrão para o `Integer` tipo de dados. Tipo de dados padrão para números de ponto flutuante são `Double`e as palavras-chave `True` e `False` especificar um `Boolean` constante.  
  
## <a name="literals-and-type-coercion"></a>Literais e coerção de tipo  
 Em alguns casos, talvez você queira forçar um literal para um determinado tipo de dados; Por exemplo, ao atribuir um valor literal inteiro muito grande a uma variável do tipo `Decimal`. O exemplo a seguir produz um erro:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 O erro resulta da representação da literal. O `Decimal` tipo de dados pode conter um valor muito grande, mas o literal implicitamente é representado como um `Long`, que não é possível.  
  
 Você pode forçar um literal para um determinado tipo de dados de duas maneiras: anexando um caractere de tipo a ele ou o colocando entre caracteres delimitadores. Um caractere de tipo ou delimitador caracteres deve imediatamente preceder e/ou suceder o literal, sem nenhum espaço intermediárias ou caracteres de qualquer tipo.  
  
 Para que o exemplo anterior funcione, você pode acrescentar o `D` digite o caractere literal, o que faz com que ele seja representado como um `Decimal`:  
  
 [!code-vb[VbVbalrConstants n º&2;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 O exemplo a seguir demonstra o uso correto dos caracteres delimitadores e caracteres de tipo:  
  
 [!code-vb[VbVbalrConstants n º&3;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 A tabela a seguir mostra os caracteres delimitadores e tipos de caracteres disponíveis no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
|Tipo de dados|Caractere delimitador|Caractere de tipo acrescentado|  
|---|---|---|  
|`Boolean`|(nenhum)|(nenhum)|  
|`Byte`|(nenhum)|(nenhum)|  
|`Char`|"|C|  
|`Date`|#|(nenhum)|  
|`Decimal`|(nenhum)|D ou @|  
|`Double`|(nenhum)|R ou #|  
|`Integer`|(nenhum)|Eu ou %|  
|`Long`|(nenhum)|L ou < /|  
|`Short`|(nenhum)|S|  
|`Single`|(nenhum)|F ou!|  
|`String`|"|(nenhum)|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes definidas pelo usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)   
 [Como: declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)   
 [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Instrução Option Explicit](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
