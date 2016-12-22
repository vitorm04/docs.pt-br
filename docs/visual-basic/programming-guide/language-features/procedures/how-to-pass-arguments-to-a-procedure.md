---
title: "Como passar argumentos para um procedimento (Visual Basic) | Microsoft Docs"
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
  - "transmissão de argumentos, procedimentos"
  - "argumentos [Visual Basic], transmitindo para procedimentos"
  - "argumentos de procedimento"
  - "parâmetros de procedimento"
  - "procedimentos, argumentos"
  - "procedimentos, Chamando "
  - "procedimentos, parâmetros"
  - "código do Visual Basic, procedimentos"
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como passar argumentos para um procedimento (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você chamar um procedimento, siga o nome do procedimento com um lista de argumentos entre parênteses.  Forneça um argumento correspondente a cada parâmetro necessário que o procedimento define, e, opcionalmente, você pode fornecer argumentos para os parâmetros `Optional`.  Se você não fornecer um parâmetro `Optional` na chamada, você deverá incluir uma vírgula para marcar seu lugar na lista de argumentos, se você estiver fornecendo quaisquer argumentos subsequentes.  
  
 Se você pretende passar um argumento de um tipo de dados diferente do seu parâmetro correspondente, como `Byte` para `String`, você pode definir a opção de verificação de tipo \([Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) para `Off`.  Se `Option Strict` estiver `On`, você deve usar conversões ampliadoras ou palavras\-chave para conversão explícita.  Para obter mais informações, consulte [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [Funções de conversão do tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Para obter mais informações, consulte [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md).  
  
### Para passar um ou mais argumentos para um procedimento  
  
1.  Na instrução de chamada, siga o nome procedimento com parênteses.  
  
2.  Dentro dos parênteses, coloque um lista de argumentos.  Incluía um argumento para cada parâmetro necessário que o procedimento define e separe os argumentos com vírgulas.  
  
3.  Verifique se cada argumento é uma expressão válida que resulta em um tipo de dados conversível para o tipo que o procedimento define para o parâmetro correspondente.  
  
4.  Se um parâmetro for definido como [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md), você pode incluí\-lo na lista de argumentos ou omiti\-lo.  Se você o omitir, o procedimento usa o valor padrão declarado para esse parâmetro.  
  
5.  Se você omitir um argumento para um parâmetro `Optional` e houver outro parâmetro depois, na lista de parâmetros, você pode marcar o local do argumento omitido por uma vírgula extra na lista de argumentos.  
  
     O exemplo a seguir chama o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> função.  
  
     [!code-vb[VbVbcnProcedures#34](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     O exemplo anterior fornece o primeiro argumento necessário, que é a sequência de caracteres da mensagem a ser exibida.  Ele omite um argumento para o segundo parâmetro opcional, que especifica os botões a serem exibidos na caixa de mensagem.  Como a chamada não fornece um valor, `MsgBox` usa o valor padrão, `MsgBoxStyle.OKOnly`, que exibe apenas um botão **OK**.  
  
     A segunda vírgula na lista de argumentos marca o local do segundo argumento omitido, e a última sequência de caracteres é passada para o terceiro parâmetro opcional de `MsgBox`, que é o texto a ser exibido na barra de título.  
  
## Consulte também  
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como definir um parâmetro para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Procedimentos recursivos](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programação orientada a objeto](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)