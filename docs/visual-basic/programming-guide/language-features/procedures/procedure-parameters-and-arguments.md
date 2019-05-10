---
title: Parâmetros e argumentos de procedimento (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 08bb05f681d5f795bc448ddc62976d7675696023
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638842"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Parâmetros e argumentos de procedimento (Visual Basic)
Na maioria dos casos, um procedimento precisa de algumas informações sobre as circunstâncias em que ele tiver sido chamado. Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada. Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando você chamá-lo.  
  
 Um *parâmetro* representa um valor que o procedimento espera que você forneça quando você chamá-lo. Declaração do procedimento define seus parâmetros.  
  
 Você pode definir um procedimento sem parâmetros, um parâmetro ou mais de um. A parte da definição do procedimento que especifica os parâmetros é chamada de *lista de parâmetros*.  
  
 Uma *argumento* representa o valor fornecido para um parâmetro de procedimento quando você chama o procedimento. O código de chamada fornece os argumentos quando ele chama o procedimento. A parte da chamada de procedimento que especifica os argumentos é chamada a *lista de argumentos*.  
  
 A ilustração a seguir mostra o código chamando o procedimento `safeSquareRoot` de dois locais diferentes. A primeira chamada passa o valor da variável `x` (4.0) para o parâmetro `number`e o valor de retorno `root` (2.0) é atribuído à variável `y`. A segunda chamada passa o valor literal 9.0 para `number`e atribui o valor de retorno (3.0) à variável `z`.  
  
 ![Diagrama que mostra a passar um argumento para um parâmetro](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 Para obter mais informações, consulte [diferenças entre parâmetros e argumentos](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Tipo de dados de parâmetro  
 Você define um tipo de dados para um parâmetro usando o `As` cláusula na sua declaração. Por exemplo, a seguinte função aceita uma cadeia de caracteres e um inteiro.  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 Se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `Off,` o `As` cláusula é opcional, exceto que, se qualquer outro parâmetro usa a ele, todos os parâmetros devem usá-lo. Se a verificação de tipo está `On`, o `As` cláusula é necessária para todos os parâmetros de procedimento.  
  
 Se o código de chamada espera que fornecer um argumento com um tipo de dados diferente do seu parâmetro correspondente, tal como `Byte` para um `String` parâmetro, ele deve fazer o seguinte:  
  
- Forneça apenas os argumentos com tipos de dados ampliam com o tipo de dados de parâmetro;  
  
- Definir `Option Strict Off` para permitir conversões de estreitamento implícitas; ou  
  
- Use uma palavra-chave de conversão para converter explicitamente o tipo de dados.  
  
### <a name="type-parameters"></a>Parâmetros de tipo  
 Um *procedimento genérico* também define um ou mais *parâmetros de tipo* , além de seus parâmetros normais. Um procedimento genérico permite que o código de chamada passar diferentes tipos de dados cada vez que ele chama o procedimento, portanto, ele pode personalizar os tipos de dados para os requisitos de cada chamada individual. Ver [procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Como: Definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md)
- [Como: Passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
