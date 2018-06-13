---
title: Como passar argumentos para um procedimento (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: f393f17f87c5920fb9bfa2a2097c09d48bebdc16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650586"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Como passar argumentos para um procedimento (Visual Basic)
Quando você chama um procedimento, você pode seguir o nome do procedimento com uma lista de argumentos entre parênteses. Forneça um argumento correspondente a cada parâmetro necessário que o procedimento define, e, opcionalmente, você pode fornecer argumentos para o `Optional` parâmetros. Se você não fornecer um `Optional` parâmetro na chamada, você deve incluir uma vírgula para marcar seu lugar na lista de argumentos, se você estiver fornecendo argumentos subsequentes.  
  
 Se você pretende passar um argumento de um tipo de dados diferente do seu parâmetro correspondente, como `Byte` para `String`, você pode definir a opção de verificação de tipo ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) para `Off`. Se `Option Strict` é `On`, você deve usar conversões ampliadoras ou palavras-chave de conversão explícita. Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Para obter mais informações, consulte [argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Para passar um ou mais argumentos para um procedimento  
  
1.  Na instrução de chamada, siga o nome do procedimento com parênteses.  
  
2.  Dentro dos parênteses, coloque uma lista de argumentos. Incluir um argumento para cada parâmetro necessário que o procedimento define e separe-os com vírgulas.  
  
3.  Verifique se que cada argumento é uma expressão válida que é avaliada como um tipo de dados conversível para o tipo de procedimento define para o parâmetro correspondente.  
  
4.  Se um parâmetro for definido como [opcional](../../../../visual-basic/language-reference/modifiers/optional.md), você pode incluí-lo na lista de argumentos ou omiti-lo. Se você omiti-lo, o procedimento usa o valor padrão definido para esse parâmetro.  
  
5.  Se você omitir um argumento para um `Optional` parâmetro e houver outro parâmetro depois, na lista de parâmetros, você pode marcar o local do argumento omitido por uma vírgula extra na lista de argumentos.  
  
     O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> função.  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     O exemplo anterior fornece o primeiro argumento necessário, que é a cadeia de caracteres de mensagem a ser exibida. Ele omite um argumento para o segundo parâmetro opcional, que especifica os botões a serem exibidos na caixa de mensagem. Como a chamada não fornece um valor, `MsgBox` usa o valor padrão, `MsgBoxStyle.OKOnly`, que exibe apenas uma **Okey** botão.  
  
     A segunda vírgula na lista de argumentos marca o local do segundo argumento omitido, e a última cadeia de caracteres é passada para o terceiro parâmetro opcional de `MsgBox`, que é o texto a ser exibido na barra de título.  
  
## <a name="see-also"></a>Consulte também

 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Como definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Procedimentos Recursivos](./recursive-procedures.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Programação orientada a objeto (Visual Basic)](../../concepts/object-oriented-programming.md)  
