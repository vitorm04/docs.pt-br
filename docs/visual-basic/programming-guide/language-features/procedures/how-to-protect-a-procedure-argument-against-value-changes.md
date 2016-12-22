---
title: "Como proteger um argumento de procedimento contra altera&#231;&#245;es de valor (Visual Basic) | Microsoft Docs"
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
  - "procedimentos, Chamando "
  - "procedimentos, parâmetros"
  - "código do Visual Basic, procedimentos"
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como proteger um argumento de procedimento contra altera&#231;&#245;es de valor (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Se um procedimento declara um parâmetro como [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece uma referência direta ao elemento de programação subjacente do argumento no código de chamada do código do procedimento.  Isso permite que o procedimento para alterar o valor subjacente do argumento no código de chamada.  Em alguns casos, o código de chamada talvez queira proteger contra tal alteração.  
  
 Você sempre pode proteger um argumento de alteração, declarando o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) no procedimento.  Se você quiser ser capaz de alterar um determinado argumento em alguns casos, mas não outros, você pode declará\-lo `ByRef` e deixe o código de chamada para determinar o mecanismo de passagem em cada chamada.  Ele faz isso colocando o argumento correspondente entre parênteses devem passar por valor ou não envolve em parênteses devem passar por referência.  Para mais informações, consulte [Como forçar um argumento a ser passado por Valor](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md).  
  
## Exemplo  
 O exemplo a seguir mostra dois procedimentos que tenham uma variável de matriz e operam em seus elementos.  O procedimento `increase` simplesmente adiciona um para cada elemento.  O procedimento `replace` atribui o parâmetro `a()` uma nova matriz e, em seguida, adiciona um para cada elemento.  No entanto, a reatribuição não afeta a variável de matriz subjacente no código de chamada.  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 Exibe o primeiro `MsgBox` chamada " após increase\(n\): 11 21, 31, 41".  Porque a matriz  `n`  é um tipo de referência,  `replace`  pode alterar seus membros, mesmo que `ByVal` seja a mecanismo de passagem.  
  
 A segunda `MsgBox` chamada exibe " Após Replace\(n\): 11, 21, 31, 41.  Porque `n` é passado `ByVal`, `replace` não é possível modificar a variável `n` no código de chamada, atribuindo\-lhe uma nova matriz.  Quando `replace` cria a nova instância de matriz `k` e a atribui à variável local `a`, ele perde a referência a `n` passado pelo código de chamada.  Quando ele se transformar os membros do `a`, apenas o array local `k` é afetado.  Portanto, `replace` não incrementa os valores da matriz `n` no código de chamada.  
  
## Compilando o código  
 O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor.  No entanto, é boa prática de programação incluir a palavra\-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) com cada parâmetro declarado.  Isso facilita a leitura seu código.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Diferenças entre argumentos modificáveis e não modificáveis](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Diferenças entre passar um argumento por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [Como alterar o valor de um argumento de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [Como forçar um argumento a ser passado por Valor](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)   
 [Passando argumentos por posição e nome](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)