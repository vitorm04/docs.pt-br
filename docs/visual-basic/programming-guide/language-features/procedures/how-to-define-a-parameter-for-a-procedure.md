---
title: Como definir um parâmetro para um procedimento (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: b058f593b8672da449dac250947563c75c8386bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651107"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Como definir um parâmetro para um procedimento (Visual Basic)
Um *parâmetro* permite que o código de chamada passar um valor para o procedimento quando ele chama. Você declara cada parâmetro para um procedimento da mesma maneira que você declarar uma variável, especificando seu nome e tipo de dados. Você também especificar o mecanismo de passagem, e se o parâmetro é opcional.  
  
 Para obter mais informações, consulte [argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Para definir um parâmetro de procedimento  
  
1.  Na declaração do procedimento, adicione o nome de parâmetro à lista de parâmetros do procedimento, separando-o de outros parâmetros por vírgulas.  
  
2.  Decida o tipo de dados do parâmetro.  
  
3.  Siga o nome do parâmetro com um `As` cláusula para especificar o tipo de dados.  
  
4.  Decida o mecanismo de passagem que você deseja para o parâmetro. Normalmente você passar um parâmetro por valor, a menos que você deseja que o procedimento seja capaz de alterar seu valor no código de chamada.  
  
5.  Preceder o nome do parâmetro com [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para especificar o mecanismo de passagem. Para obter mais informações, consulte [diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Se o parâmetro é opcional, preceda o mecanismo de passagem com [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) e siga o tipo de dados de parâmetro com um sinal de igual (`=`) e um valor padrão.  
  
     O exemplo a seguir define o contorno de uma `Sub` procedimento com três parâmetros. Os dois primeiros são necessários e a terceira é opcional. Declarações de parâmetro são separadas na lista de parâmetros por vírgulas.  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     O primeiro parâmetro aceita um `customer` objeto, e `updateCustomer` pode atualizar diretamente a variável passada para `c` porque o argumento é passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). O procedimento não pode alterar os valores dos dois últimos argumentos porque eles são passados [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Se o código de chamada não fornecer um valor para o `level` parâmetro, Visual Basic define como o valor padrão de 0.  
  
     Se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `Off`, o `As` cláusula é opcional quando você define um parâmetro. No entanto, se qualquer outro parâmetro usa um `As` cláusula, todos eles devem usá-la. Se a opção de verificação de tipo é `On`, o `As` cláusula é necessária para cada definição de parâmetro.  
  
     Especificar tipos de dados para todos os elementos de programação é conhecido como *tipagem forte*. Quando você define `Option Strict On`, Visual Basic impõe tipagem forte. Isso é altamente recomendável, pelos seguintes motivos:  
  
    -   Ele permite o suporte ao IntelliSense para suas variáveis e parâmetros. Isso permite que você veja suas propriedades e outros membros conforme você digita no seu código.  
  
    -   Isso permite que o compilador realizar a verificação de tipo. Isso ajuda a obter declarações que podem falhar em tempo de execução devido a erros, como o estouro. Também captura chamadas para métodos em objetos que não dão suporte a eles.  
  
    -   Isso resulta em execução mais rápida do seu código. Uma razão para isso é que se você não especificar um tipo de dados para um elemento de programação, o compilador do Visual Basic atribui o `Object` tipo. Seu código compilado pode precisar converter entre `Object` e outros tipos de dados, o que reduz o desempenho.  
  
## <a name="see-also"></a>Consulte também

 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Procedimentos Recursivos](./recursive-procedures.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Programação orientada a objeto (Visual Basic)](../../concepts/object-oriented-programming.md)  
