---
title: "Par&#226;metros opcionais (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "argumentos [Visual Basic], optional"
  - "argumentos nomeados, e argumentos opcionais"
  - "argumentos opcionais"
  - "argumentos opcionais, e argumentos nomeados"
  - "palavra-chave Optional, argumentos opcionais"
  - "parâmetros opcionais"
  - "parâmetros, optional"
  - "procedimentos, argumentos opcionais"
  - "código do Visual Basic, procedimentos"
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metros opcionais (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode especificar que um parâmetro de procedimento é opcional e nenhum argumento precisa ser fornecido para ele quando o procedimento é chamado.  *Parâmetros opcionais* são indicados pela palavra\-chave `Optional` na definição do procedimento.  As seguintes regras se aplicam:  
  
-   Cada parâmetro opcional na definição do procedimento deve especificar um valor padrão.  
  
-   O valor padrão para um parâmetro opcional deve ser uma expressão constante.  
  
-   Todo parâmetro após um parâmetro opcional na definição do procedimento também deve ser opcional.  
  
 A sintaxe a seguir mostra uma declaração de procedimento com um parâmetro opcional:  
  
```  
Sub sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## Chamando procedimentos com parâmetros opcionais  
 Ao chamar um procedimento com um parâmetro opcional, você pode escolher se deseja fornecer o argumento.  Caso contrário, o procedimento usa o valor padrão declarado para esse parâmetro.  
  
 Ao omitir um ou mais argumentos opcionais no lista de argumentos, você use sucessivas vírgulas para marcar as posições.  A chamada de exemplo a seguir fornece o primeiro e o quarto argumentos, mas não o segundo ou terceiro:  
  
```  
  
sub name(argument 1, , , argument 4)  
```  
  
 O exemplo a seguir faz várias chamadas para a função `MsgBox`.  `MsgBox` tem um parâmetro obrigatório e dois parâmetros opcionais.  
  
 A primeira chamada para `MsgBox` fornece todos os três argumentos na ordem que `MsgBox` os define.  A segunda chamada fornece apenas o argumento necessário.  A terceira e a quarta chamadas fornecem o primeiro e o terceiro argumentos.  A terceira chamada faz isso por posição, e a quarta chamada faz isso por nome.  
  
 [!code-vb[VbVbcnProcedures#47](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## Determinando se um argumento opcional está presente  
 Um procedimento não pode detectar no tempo de execução se um determinado argumento foi omitido ou o código de chamada forneceu explicitamente o valor padrão.  Se você precisar fazer essa distinção, defina um valor improvável como o padrão.  O procedimento a seguir define o parâmetro opcional `office` e testa seu valor padrão, `QJZ`, para ver se ele foi omitido na chamada:  
  
 [!code-vb[VbVbcnProcedures#46](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 Se o parâmetro opcional for um tipo de referência como `String`, você poderá usar `Nothing` como valor padrão, desde que não seja um valor esperado para o argumento.  
  
## Parâmetros opcionais e sobrecarga  
 Outra maneira de definir um procedimento com parâmetros opcionais é usar a sobrecarga.  Se você tiver um parâmetro opcional, poderá definir duas versões sobrecarregadas do procedimento, uma aceitando o parâmetro e outra sem ele.  Essa abordagem torna\-se mais complicada à medida que o número de parâmetros opcionais aumenta.  No entanto, sua vantagem é que você pode ter certeza absoluta se o programa de chamada forneceu cada argumento opcional.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Passando argumentos por posição e nome](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Matrizes de parâmetros](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)