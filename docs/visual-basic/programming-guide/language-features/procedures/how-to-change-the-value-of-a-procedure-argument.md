---
title: "Como alterar o valor de um argumento de procedimento (Visual Basic) | Microsoft Docs"
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
  - "argumentos [Visual Basic], ByRef"
  - "argumentos [Visual Basic], ByVal"
  - "argumentos [Visual Basic], alterando valor"
  - "argumentos [Visual Basic], passagem por referência"
  - "argumentos [Visual Basic], transmitindo por valor"
  - "argumentos de procedimento"
  - "parâmetros de procedimento"
  - "procedimentos, argumentos"
  - "procedimentos, parâmetros"
  - "código do Visual Basic, procedimentos"
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como alterar o valor de um argumento de procedimento (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você chamar um procedimento, cada argumento que você fornecer corresponde a um dos parâmetros definidos no procedimento.  Em alguns casos, o código do procedimento pode alterar o valor subjacente um argumento no código de chamada.  Em outros casos, o procedimento pode alterar apenas sua cópia local de um argumento.  
  
 Quando você chamar o procedimento, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Faz uma cópia local de cada argumento que é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  Para cada argumento passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md),[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece o código do procedimento uma referência direta para o elemento de programação subjacente o argumento o código de chamada.  
  
 Se o elemento BASE no código de chamada é um elemento modificável e o argumento é passado `ByRef`,o código do procedimento pode usar a referência direta para alterar valor do elemento no código de chamada.  
  
## Alterando o valor Underlying  
  
#### Para alterar o valor subjacente de um argumento procedimento no código de chamada  
  
1.  Na declaração do procedimento, especifique [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para o parâmetro correspondente ao argumento.  
  
2.  No código de chamada, passe um elemento de programação modificável como o argumento.  
  
3.  No código de chamada, não coloque o argumento entre parênteses na lista de argumentos.  
  
4.  No código de procedimento, usar o nome do parâmetro para atribuir um valor para o elemento BASE no código de chamada.  
  
 Consulte o exemplo mais para baixo para ver uma demonstração.  
  
## Alterando cópias locais  
 Se o elemento BASE no código de chamada é um elemento nonmodifiable, ou se o argumento é passado `ByVal`,o procedimento não é possível alterar o valor no código de chamada.  No entanto, o procedimento pode alterar sua cópia local de um argumento.  
  
#### Para alterar a cópia de um argumento procedimento no código de procedimento  
  
1.  Na declaração do procedimento, especifique [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) para o parâmetro correspondente ao argumento.  
  
     \-  ou  \-  
  
     No código de chamada, não coloque o argumento entre parênteses na lista de argumentos.  Isso força [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para passar o argumento por valor, mesmo se o parâmetro correspondente `ByRef` especifica.  
  
2.  No código de procedimento, usar o nome do parâmetro para atribuir um valor para a cópia local do argumento.  O valor subjacente no código de chamada não é alterado.  
  
## Exemplo  
 O exemplo a seguir mostra dois procedimentos que tenham uma variável de matriz e operam em seus elementos.  O procedimento `increase` simplesmente adiciona um para cada elemento.  O procedimento `replace` atribui o parâmetro `a()` uma nova matriz e, em seguida, adiciona um para cada elemento.  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 Exibe o primeiro `MsgBox` chamada " após increase\(n\): 11 21, 31, 41".  Porque a matriz  `n`  é um tipo de referência,  `replace`  pode alterar seus membros, mesmo que `ByVal` seja a mecanismo de passagem.  
  
 A segunda `MsgBox` chamada exibe " Após Replace\(n\): 101, 201, 301".  Como `n` é passado `ByRef`, `replace`  pode modificar a variável  `n`  no código de chamada e atribuir uma nova matriz para ele.  Como  `n`  é um tipo de referência,  `replace`  também pode alterar seus membros.  
  
 Você pode impedir modificando a variável próprio no código de chamada de procedimento.  Consulte [Como proteger um argumento de procedimento contra alterações de valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## Compilando o código  
 Quando uma variável é passada por referência, você deve usar a palavra\-chave  `ByRef` para especificar esse mecanismo.  
  
 O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor.  No entanto, é boa prática de programação incluir a palavra\-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) com cada parâmetro declarado.  Isso facilita a leitura seu código.  
  
## Segurança do .NET Framework  
 Sempre há um risco potencial em permitir que um procedimento altere o valor subjacente a um argumento no código de chamada.  Certifique\-se de que você espera que esse valor seja alterado e esteja preparado para verificá\-lo para validade antes de usá\-lo.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Diferenças entre argumentos modificáveis e não modificáveis](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Diferenças entre passar um argumento por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [Como proteger um argumento de procedimento contra alterações de valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Como forçar um argumento a ser passado por Valor](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)   
 [Passando argumentos por posição e nome](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)