---
title: "Parâmetros de procedimento e argumentos (Visual Basic) | Documentos do Microsoft"
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
- procedures, arguments
- procedures, argument lists
- values, passing to procedures
- arguments [Visual Basic], passing
- procedures, parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters, Visual Basic procedures
- parameters, lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists
- Visual Basic code, parameter lists
- argument lists
- procedures, parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: d09676ca448b8f0d4efbee4643f9470e53ddeece
ms.lasthandoff: 03/13/2017

---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Parâmetros e argumentos de procedimento (Visual Basic)
Na maioria dos casos, um procedimento precisa de algumas informações sobre as circunstâncias em que ele foi chamado. Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada. Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando chamá-lo.  
  
 A *parâmetro* representa um valor que o procedimento espera que você forneça quando você chamá-lo. Declaração do procedimento define seus parâmetros.  
  
 Você pode definir um procedimento com sem parâmetros, um parâmetro ou mais de um. A parte da definição do procedimento que especifica os parâmetros é chamada de *lista de parâmetros*.  
  
 Um *argumento* representa o valor fornecido para um parâmetro de procedimento quando você chamar o procedimento. O código de chamada fornece os argumentos quando ele chama o procedimento. A parte da chamada de procedimento que especifica os argumentos é chamada de *lista de argumentos*.  
  
 A ilustração a seguir mostra código chamando o procedimento `safeSquareRoot` de dois lugares diferentes. A primeira chamada passa o valor da variável `x` (4.0) para o parâmetro `number`e o valor de retorno em `root` (2.0) é atribuído à variável `y`. A segunda chamada passa o valor literal 9.0 para `number`e atribui o valor de retorno (3.0) à variável `z`.  
  
 ![Diagrama de gráfico de passagem de argumento para o parâmetro](./media/parametersargue.gif "ParametersArgue")  
Passar um argumento para um parâmetro  
  
 Para obter mais informações, consulte [as diferenças entre parâmetros e argumentos](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Tipo de dados do parâmetro  
 Definir um tipo de dados para um parâmetro usando o `As` cláusula na sua declaração. Por exemplo, a seguinte função aceita uma cadeia de caracteres e um número inteiro.  
  
 [!code-vb[32 VbVbcnProcedures](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 Se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `Off,` de `As` cláusula é opcional, exceto que se qualquer outro parâmetro usa a ele, todos os parâmetros devem usá-lo. Se a verificação de tipo é `On`, o `As` cláusula é necessária para todos os parâmetros de procedimento.  
  
 Se o código de chamada espera fornecer um argumento com um tipo de dados diferente do seu parâmetro correspondente, como `Byte` para um `String` parâmetro, ele deve fazer o seguinte:  
  
-   Forneça apenas os argumentos com tipos de dados que ampliam para o tipo de dados do parâmetro;  
  
-   Defina `Option Strict Off` para permitir conversões de estreitamento implícitas; ou  
  
-   Use uma palavra-chave de conversão para converter explicitamente o tipo de dados.  
  
### <a name="type-parameters"></a>Parâmetros de tipo  
 A *procedimento genérico* também define um ou mais *parâmetros de tipo* além de seus parâmetros normais. Um procedimento genérico permite que o código de chamada passe diferentes tipos de dados cada vez que ele chama o procedimento, portanto ele pode personalizar os tipos de dados para os requisitos de cada chamada individual. Consulte [procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de função](./function-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Como: definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md)   
 [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
