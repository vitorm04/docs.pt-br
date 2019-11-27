---
title: Como definir um parâmetro para um procedimento
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 411959a7be92ea49a59558b508e992bfba8eff95
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344881"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Como definir um parâmetro para um procedimento (Visual Basic)
Um *parâmetro* permite que o código de chamada transmita um valor para o procedimento ao chamá-lo. Você declara cada parâmetro para um procedimento da mesma maneira que declara uma variável, especificando seu nome e tipo de dados. Você também especifica o mecanismo de passagem e se o parâmetro é opcional.  
  
 Para obter mais informações, consulte [parâmetros e argumentos de procedimento](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Para definir um parâmetro de procedimento  
  
1. Na declaração de procedimento, adicione o nome do parâmetro à lista de parâmetros do procedimento, separando-o de outros parâmetros por vírgulas.  
  
2. Decida o tipo de dados do parâmetro.  
  
3. Siga o nome do parâmetro com uma cláusula `As` para especificar o tipo de dados.  
  
4. Decida o mecanismo de passagem que você deseja para o parâmetro. Normalmente, você passa um parâmetro por valor, a menos que queira que o procedimento seja capaz de alterar seu valor no código de chamada.  
  
5. Preceda o nome do parâmetro com [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para especificar o mecanismo de passagem. Para obter mais informações, consulte [diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6. Se o parâmetro for opcional, preceda o mecanismo de passagem com [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) e siga o tipo de dados de parâmetro com um sinal de igual (`=`) e um valor padrão.  
  
     O exemplo a seguir define o contorno de um procedimento `Sub` com três parâmetros. Os dois primeiros são obrigatórios e o terceiro é opcional. As declarações de parâmetro são separadas na lista de parâmetros por vírgulas.  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     O primeiro parâmetro aceita um objeto `customer` e `updateCustomer` pode atualizar diretamente a variável passada para `c` porque o argumento é passado como [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). O procedimento não pode alterar os valores dos últimos dois argumentos porque eles são passados por [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Se o código de chamada não fornecer um valor para o parâmetro `level`, Visual Basic o definirá como o valor padrão de 0.  
  
     Se a opção de verificação de tipo ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) for `Off`, a cláusula `As` será opcional quando você definir um parâmetro. No entanto, se qualquer parâmetro usar uma cláusula `As`, todos eles deverão usá-la. Se a opção de verificação de tipo for `On`, a cláusula `As` será necessária para cada definição de parâmetro.  
  
     Especificar tipos de dados para todos os elementos de programação é conhecido como tipagem *forte*. Quando você define `Option Strict On`, Visual Basic impõe tipagem forte. Isso é altamente recomendável, pelos seguintes motivos:  
  
    - Ele habilita o suporte IntelliSense para suas variáveis e parâmetros. Isso permite que você veja suas propriedades e outros membros enquanto digita em seu código.  
  
    - Ele permite que o compilador execute a verificação de tipo. Isso ajuda a capturar instruções que podem falhar em tempo de execução devido a erros como overflow. Ele também captura chamadas para métodos em objetos que não dão suporte a eles.  
  
    - Isso resulta em uma execução mais rápida do seu código. Um motivo para isso é que se você não especificar um tipo de dados para um elemento de programação, o compilador Visual Basic atribuirá a ele o tipo de `Object`. O código compilado pode ter que fazer a conversão entre `Object` e outros tipos de dados, o que reduz o desempenho.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Função](./function-procedures.md)
- [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Procedimentos Recursivos](./recursive-procedures.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programação orientada a objeto (Visual Basic)](../../concepts/object-oriented-programming.md)
