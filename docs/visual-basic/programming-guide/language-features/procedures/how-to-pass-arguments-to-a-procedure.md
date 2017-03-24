---
title: 'Como: passar argumentos para um procedimento (Visual Basic) | Documentos do Microsoft'
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
- arguments [Visual Basic], passing to procedures
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures, calling
- argument passing, procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: ddccd476b2347368d0435f637edf3882db306f45
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Como passar argumentos para um procedimento (Visual Basic)
Quando você chama um procedimento, você pode seguir o nome do procedimento com uma lista de argumentos entre parênteses. Forneça um argumento correspondente a cada parâmetro necessário que o procedimento define, e, opcionalmente, você pode fornecer argumentos para o `Optional` parâmetros. Se você não fornecer um `Optional` parâmetro na chamada, você deve incluir uma vírgula para marcar seu lugar na lista de argumentos, se você estiver fornecendo quaisquer argumentos subsequentes.  
  
 Se você pretende passar um argumento de um tipo de dados diferente do seu parâmetro correspondente, como `Byte` para `String`, você pode definir a opção de verificação de tipo ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) para `Off`. Se `Option Strict` é `On`, você deve usar conversões ampliadoras ou palavras-chave de conversão explícita. Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Para obter mais informações, consulte [argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Para passar um ou mais argumentos para um procedimento  
  
1.  Na instrução de chamada, siga o nome do procedimento com parênteses.  
  
2.  Dentro dos parênteses, coloque uma lista de argumentos. Incluir um argumento para cada parâmetro necessário que o procedimento define e separe-os com vírgulas.  
  
3.  Verifique se que cada argumento é uma expressão que é avaliada como um tipo de dados conversível para o tipo que o procedimento define para o parâmetro correspondente.  
  
4.  Se um parâmetro for definido como [opcional](../../../../visual-basic/language-reference/modifiers/optional.md), você pode incluí-lo na lista de argumentos ou omiti-lo. Se você omitir, o procedimento usa o valor padrão definido para esse parâmetro.  
  
5.  Se você omitir um argumento para um `Optional` parâmetro e houver outro parâmetro depois, na lista de parâmetros, você pode marcar o local do argumento omitido por uma vírgula extra na lista de argumentos.  
  
     A exemplo a seguir chama o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>função.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
     [!code-vb[VbVbcnProcedures&#34;](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     O exemplo anterior fornece o primeiro argumento necessário, que é a cadeia de caracteres de mensagem a ser exibida. Ele omite um argumento para o segundo parâmetro opcional, que especifica os botões a serem exibidos na caixa de mensagem. Como a chamada não fornece um valor, `MsgBox` usa o valor padrão, `MsgBoxStyle.OKOnly`, que exibe apenas uma **Okey** botão.  
  
     A segunda vírgula na lista de argumentos marca o local do segundo argumento omitido, e última sequência de caracteres é passada para o terceiro parâmetro opcional de `MsgBox`, que é o texto a ser exibido na barra de título.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de função](./function-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Como: definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Procedimentos recursivos](./recursive-procedures.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programação Orientada a Objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
