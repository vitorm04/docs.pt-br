---
title: "Par&#226;metros e argumentos de procedimento (Visual Basic) | Microsoft Docs"
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
  - "listas de argumentos"
  - "argumentos [Visual Basic], passando"
  - "argumentos [Visual Basic], procedimentos"
  - "argumentos [Visual Basic], procedimentos do Visual Basic"
  - "listas de parâmetros"
  - "parâmetros, listas"
  - "parâmetros, procedimentos do Visual Basic"
  - "procedimentos, listas de argumentos"
  - "procedimentos, argumentos"
  - "procedimentos, listas de parâmetros"
  - "procedimentos, parâmetros"
  - "Valores, transmitindo para procedimentos"
  - "código do Visual Basic, listas de argumentos"
  - "código do Visual Basic, listas de parâmetros"
  - "código do Visual Basic, procedimentos"
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metros e argumentos de procedimento (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Na maioria dos casos, um procedimento precisa de algumas informações sobre as circunstâncias em que ele foi chamado.  Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada.  Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando você o chama.  
  
 A  *parâmetro* representa um valor que o procedimento espera que você forneça quando você chamá\-lo.  A declaração do procedimento define os seus parâmetros.  
  
 Você pode definir um procedimento sem parâmetros, um parâmetro, ou mais de um.  A parte da definição do procedimento que especifica os parâmetros é chamada a  *lista de parâmetros*.  
  
 Um  *argumento* representa o valor fornecido para um parâmetro de procedimento, quando você chama o procedimento.  O código de chamada fornece os argumentos quando chama o procedimento.  A parte da chamada de procedimento que especifica os argumentos é chamada a  *lista de argumentos*.  
  
 A ilustração a seguir mostra o código para chamar o procedimento `safeSquareRoot` em dois locais diferentes.  A primeira chamada passa o valor da variável `x` \(4.0\) para o parâmetro `number`e o valor de retorno de `root` \(2.0\) é atribuído à variável `y`.  A segunda chamada passa o valor literal 9.0 para `number`e atribui o valor de retorno \(3.0\), a variável `z`.  
  
 ![Diagrama gráfico de passar o argumento para o parâmetro](../../../../visual-basic/programming-guide/language-features/procedures/media/parametersargue.png "ParametersArgue")  
Passar um argumento para um parâmetro  
  
 Para obter mais informações, consulte [Diferenças entre parâmetros e argumentos](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
## Tipo de dados de parâmetro  
 Você define um tipo de dados para um parâmetro usando a `As` cláusula na sua declaração.  Por exemplo, a seguinte função aceita uma seqüência e um número inteiro.  
  
 [!code-vb[VbVbcnProcedures#32](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 Se o tipo de verificação Alternar \([Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) é `Off,` a `As` cláusula é opcional, exceto que se qualquer um parâmetro usa\-lo, todos os parâmetros devem usá\-lo.  Se a verificação de tipo é `On`, o `As` cláusula é obrigatória para todos os parâmetros de procedimento.  
  
 Se o código de chamada espera fornecer um argumento com um tipo de dados diferente do seu parâmetro correspondente, como `Byte` para um `String` parâmetro, ele deve fazer um dos seguintes:  
  
-   Fonte somente os argumentos com tipos de dados que aumentarão para o parâmetro de tipo de dados;  
  
-   Definir `Option Strict Off` para permitir conversões implícitas de restrição; ou  
  
-   Use uma palavra\-chave de conversão para converter explicitamente o tipo de dados.  
  
### Parâmetros de tipo  
 A  *procedimento genérico* também define um ou mais  *parâmetros de tipo* com seus parâmetros normais.  Um procedimento genérico permite que o código de chamada passar cada vez que ele chama o procedimento, portanto, os tipos de dados para os requisitos de cada chamada individual podem ser adaptadas a diferentes tipos de dados.  Consulte [Procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como definir um parâmetro para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)