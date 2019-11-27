---
title: Como passar argumentos para um procedimento
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
ms.openlocfilehash: 0267eed7c145988d61de715fd661bd4906d8d57d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344839"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Como passar argumentos para um procedimento (Visual Basic)
Ao chamar um procedimento, você segue o nome do procedimento com uma lista de argumentos entre parênteses. Você fornece um argumento correspondente a cada parâmetro necessário que o procedimento define, e você pode, opcionalmente, fornecer argumentos para os parâmetros de `Optional`. Se você não fornecer um parâmetro `Optional` na chamada, deverá incluir uma vírgula para marcá-lo na lista de argumentos se estiver fornecendo argumentos subsequentes.  
  
 Se você pretende passar um argumento de um tipo de dados diferente daquele de seu parâmetro correspondente, como `Byte` para `String`, você pode definir a opção de verificação de tipo ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) como `Off`. Se `Option Strict` for `On`, você deverá usar conversões de ampliação ou palavras-chave de conversão explícita. Para obter mais informações, consulte [conversões de ampliação e estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Para obter mais informações, consulte [parâmetros e argumentos de procedimento](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Para passar um ou mais argumentos para um procedimento  
  
1. Na instrução de chamada, siga o nome do procedimento com parênteses.  
  
2. Dentro dos parênteses, coloque uma lista de argumentos. Inclua um argumento para cada parâmetro necessário que o procedimento define e separe os argumentos com vírgulas.  
  
3. Certifique-se de que cada argumento é uma expressão válida que é avaliada como um tipo de dados conversível para o tipo que o procedimento define para o parâmetro correspondente.  
  
4. Se um parâmetro for definido como [opcional](../../../../visual-basic/language-reference/modifiers/optional.md), você poderá incluí-lo na lista de argumentos ou omiti-lo. Se você omiti-lo, o procedimento usará o valor padrão definido para esse parâmetro.  
  
5. Se você omitir um argumento para um parâmetro `Optional` e houver outro parâmetro depois dele na lista de parâmetros, poderá marcar o lugar do argumento omitido por uma vírgula extra na lista de argumentos.  
  
     O exemplo a seguir chama a função Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     O exemplo anterior fornece o primeiro argumento necessário, que é a cadeia de caracteres da mensagem a ser exibida. Ele omite um argumento para o segundo parâmetro opcional, que especifica os botões a serem exibidos na caixa de mensagem. Como a chamada não fornece um valor, `MsgBox` usa o valor padrão, `MsgBoxStyle.OKOnly`, que exibe apenas um botão **OK** .  
  
     A segunda vírgula na lista de argumentos marca o lugar do segundo argumento omitido e a última cadeia de caracteres é passada para o terceiro parâmetro opcional de `MsgBox`, que é o texto a ser exibido na barra de título.  
  
## <a name="see-also"></a>Consulte também

- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Como definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Procedimentos Recursivos](./recursive-procedures.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programação orientada a objeto (Visual Basic)](../../concepts/object-oriented-programming.md)
