---
title: "Tipos de dados constante e literal (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constantes, declarando"
  - "tipos de dados [Visual Basic], declarando"
  - "declarações, tipos de dados"
  - "declarando constantes, tipos de dados literais"
  - "declarações explícitas"
  - "literais, tipo de dados de coerção"
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados constante e literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um literal é um valor que é expresso como si mesmo em vez de como um valor variável ou o resultado de uma expressão, como o número 3 ou a sequência "Alô".  Uma constante é um nome significativo que toma o lugar de um literal e mantém esse mesmo valor em todo o programa, em oposição a uma variável, cujo valor pode ser alterado.  
  
 Quando  [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e  [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar explicitamente todas as constantes com um tipo de dados.  No exemplo a seguir, o tipo de dados do `MyByte` é declarado explicitamente como tipo de dados `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Quando `Option Infer` é `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula.  O compilador determina o tipo da constante do tipo da expressão.  Um literal numérico inteiro é convertido, por padrão, para o tipo de dados `Integer`.  O tipo de dados padrão para números de ponto flutuante é `Double` e as palavras\-chave `True` e `False` especificam uma constante `Boolean`.  
  
## Coerção de Literais e Tipos  
 Em alguns casos, você talvez queira forçar um literal para um determinado tipo de dados; por exemplo, ao atribuir um valor literal inteiro muito grande a uma variável do tipo `Decimal`.  O exemplo a seguir produz um erro:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 O erro resulta da representação da literal.  O tipo de dados `Decimal` pode conter um valor muito grande, mas o literal implicitamente é representado como `Long`, o que não é possível.  
  
 Você pode forçar um literal a um determinado tipo de dados de duas maneiras: anexando um caractere de tipo a ele ou o colocando entre caracteres delimitadores.  Um caractere de tipo ou delimitador caracteres deve imediatamente preceder e\/ou suceder o literal, sem nenhum espaço intermediárias ou caracteres de qualquer tipo.  
  
 Para fazer o exemplo anterior funcionar, você pode acrescentar o caractere de tipo `D` ao literal, o que faz com que ele seja representado como um `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 O exemplo a seguir demonstra o uso correto dos caracteres delimitadores de tipo e:  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 A tabela a seguir mostra os caracteres delimitadores e tipos de caracteres disponíveis no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
||||  
|-|-|-|  
|Tipo de dados|Caracteres delimitadores|Caractere de tipo acrescentado|  
|`Boolean`|\(Nenhum\)|\(Nenhum\)|  
|`Byte`|\(Nenhum\)|\(Nenhum\)|  
|`Char`|"|C|  
|`Date`|\#|\(Nenhum\)|  
|`Decimal`|\(Nenhum\)|D ou @|  
|`Double`|\(Nenhum\)|R ou \#|  
|`Integer`|\(Nenhum\)|I ou %|  
|`Long`|\(Nenhum\)|L ou &|  
|`Short`|\(Nenhum\)|S|  
|`Single`|\(Nenhum\)|F ou \!|  
|`String`|"|\(Nenhum\)|  
  
## Consulte também  
 [Constantes definidas pelo usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)   
 [Como declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)   
 [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Instrução Option Explicit](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)