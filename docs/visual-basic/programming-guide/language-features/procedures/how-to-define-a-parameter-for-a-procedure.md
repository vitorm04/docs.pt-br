---
title: 'Como: Definir um parâmetro para um procedimento (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 01b150d70c07897f8217ed6958e3654aa28fdf51
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971787"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Como: Definir um parâmetro para um procedimento (Visual Basic)
Um *parâmetro* permite que o código de chamada passar um valor para o procedimento quando ele a chama. Você declara cada parâmetro para um procedimento da mesma maneira que você declare uma variável, especificando seu nome e tipo de dados. Você também especificar o mecanismo de passagem, e se o parâmetro é opcional.  
  
 Para obter mais informações, consulte [parâmetros de procedimento e os argumentos](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Para definir um parâmetro de procedimento  
  
1.  Na declaração do procedimento, adicione o nome do parâmetro à lista de parâmetros do procedimento, separando-o de outros parâmetros por vírgulas.  
  
2.  Decida o tipo de dados do parâmetro.  
  
3.  Siga o nome do parâmetro com um `As` cláusula para especificar o tipo de dados.  
  
4.  Decida o mecanismo de passagem que você deseja para o parâmetro. Normalmente você passa um parâmetro por valor, a menos que você deseja que o procedimento para ser capaz de alterar seu valor no código de chamada.  
  
5.  Preceda o nome de parâmetro com [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para especificar o mecanismo de passagem. Para obter mais informações, consulte [diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Se o parâmetro é opcional, preceda o mecanismo de passagem com [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) e siga o tipo de dados de parâmetro com um sinal de igual (`=`) e um valor padrão.  
  
     O exemplo a seguir define o contorno de uma `Sub` procedimento com três parâmetros. As duas primeiras são necessárias e a terceira é opcional. As declarações de parâmetro são separadas na lista de parâmetros por vírgulas.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     O primeiro parâmetro aceita um `customer` objeto, e `updateCustomer` pode atualizar diretamente a variável passada a `c` porque o argumento é passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). O procedimento não é possível alterar os valores dos dois últimos argumentos porque eles são passados [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Se o código de chamada não fornecer um valor para o `level` parâmetro, Visual Basic define como o valor padrão de 0.  
  
     Se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `Off`, o `As` cláusula é opcional quando você define um parâmetro. No entanto, se qualquer outro parâmetro usa um `As` cláusula, todos eles devem usá-lo. Se a opção de verificação de tipo estiver `On`, o `As` cláusula é necessária para cada definição de parâmetro.  
  
     Especificar tipos de dados para todos os elementos de programação é conhecido como *tipagem forte*. Quando você define `Option Strict On`, Visual Basic impõe tipagem forte. Isso é altamente recomendado, pelos seguintes motivos:  
  
    -   Ele permite que o suporte ao IntelliSense para suas variáveis e parâmetros. Isso permite que você veja suas propriedades e outros membros conforme você digita em seu código.  
  
    -   Ele permite que o compilador execute a verificação de tipo. Isso ajuda a resolver as instruções que podem falhar em tempo de execução devido a erros, como estouro. Ela também captura chamadas para métodos em objetos que não dão suporte a eles.  
  
    -   Isso resulta em uma execução mais rápida do seu código. Um motivo para isso é que se você não especificar um tipo de dados para um elemento de programação, o compilador do Visual Basic atribui a ele o `Object` tipo. Seu código compilado talvez seja necessário converter entre `Object` e outros tipos de dados, o que reduz o desempenho.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Função](./function-procedures.md)
- [Como: Passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Procedimentos Recursivos](./recursive-procedures.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programação orientada a objeto (Visual Basic)](../../concepts/object-oriented-programming.md)
