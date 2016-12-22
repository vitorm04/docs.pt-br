---
title: "Passando argumentos por valor e por refer&#234;ncia (Visual Basic) | Microsoft Docs"
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
  - "transmissão de argumentos, por valor ou por referência"
  - "argumentos [Visual Basic], transmitindo por valor ou por referência"
  - "Palavra-chave ByRef, transmitindo argumentos por referência"
  - "Palavra-chave ByVal, transmitindo argumentos por valor"
  - "argumentos de passagem, por valor ou por referência"
  - "código do Visual Basic, procedimentos"
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Passando argumentos por valor e por refer&#234;ncia (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], você pode passar um argumento para um procedimento *por valor* ou *por referência*.  Isso é conhecido como *o mecanismo*de passagem, e determina se o procedimento pode modificar o elemento de programação subjacente o argumento o código de chamada.  A declaração do procedimento determina o mecanismo de passagem de cada parâmetro especificando a palavra\-chave de [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou de [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) .  
  
## Distinções  
 Para passar um argumento para um procedimento, esteja ciente das várias com diferentes que interagem entre si:  
  
-   Se o elemento de programação subjacente modificável é ou não modificáveis  
  
-   Se o argumento é próprio modificável ou não modificáveis  
  
-   Se o argumento está sendo passado por valor ou por referência  
  
-   Se o tipo de dados do argumento é um tipo de valor ou tipo de referência  
  
 Para obter mais informações, consulte [Diferenças entre argumentos modificáveis e não modificáveis](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md) e [Diferenças entre passar um argumento por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## Escolha do mecanismo de passagem  
 Você deve escolher o mecanismo de passagem cuidadosamente para cada argumento.  
  
-   **proteção**.  Em escolher entre os dois mecanismos de passagem, o critério o mais importante é a exposição de variáveis de chamada a alteração.  A vantagem de passar um argumento `ByRef` é que o procedimento pode retornar um valor para o código de chamada através do argumento.  A vantagem de passar um argumento `ByVal` é que protege uma variável de ser alterado pelo procedimento.  
  
-   **desempenho**.  Embora o mecanismo de passagem pode afetar o desempenho do seu código, a diferença é geralmente insignificanta.  Uma exceção a essa `ByVal`é passado tipo de valor.  Em esse caso, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copia o conteúdo de dados inteiros do argumento.  Portanto, para um grande tipo de valor como uma estrutura, pode ser mais eficiente passe `ByRef`.  
  
     Para tipos de referência, somente o ponteiro para os dados é copiado \(quatro bytes em plataformas de 32 bits, oito bytes em plataformas de 64 bits\).  Portanto, você pode passar argumentos de tipo `String` ou `Object` pelo valor sem prejudicar o desempenho.  
  
## Determinar o mecanismo de passagem  
 A declaração de procedimento especifica o mecanismo de passagem de cada parâmetro.  O código de chamada não pode substituir um mecanismo de `ByVal` .  
  
 Se um parâmetro é declarado com `ByRef`, o código de chamada pode forçar o mecanismo a `ByVal` incluindo o nome do argumento entre parênteses na chamada.  Para obter mais informações, consulte [Como forçar um argumento a ser passado por Valor](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md).  
  
 O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor.  
  
## Quando passar um argumento por valor  
  
-   Se o elemento de código de chamada que é subjacente ao argumento é um elemento não modificável, declare o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  Nenhum código pode alterar o valor de um elemento não modificável.  
  
-   Se o elemento é subjacente modificável, mas você não deseja que o procedimento para poder alterar seu valor, declare o parâmetro `ByVal`.  Somente o código de chamada pode alterar o valor de um elemento modificável passado por valor.  
  
## Quando passar um argumento por referência  
  
-   Se o procedimento possui uma necessidade genuína de modificar o elemento subjacente no código de chamada, declare o parâmetro correspondente [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Se a execução correta de código depende do procedimento que alterar o elemento subjacente no código de chamada, declare o parâmetro `ByRef`.  Se você a passagem por valor, ou se o código de chamada substitui `ByRef` que passa pelo mecanismo incluindo o argumento entre parênteses, a chamada de procedimento pode produzir resultados inesperados.  
  
## Exemplo  
  
### Descrição  
 O exemplo a seguir ilustra quando passar argumentos por valor e quando os passa por referência.  o procedimento `Calculate` tem `ByVal` e um parâmetro de `ByRef` .  Dada a taxa de juros, `rate`, e um, importe `debt`, a tarefa de procedimento é calcular um novo valor para `debt` que é o resultado de aplicar a taxa de juros para o valor original de `debt`.  Porque `debt` é um parâmetro de `ByRef` , o novo total é refletido no valor do argumento no código de chamada que corresponde a `debt`.  o parâmetro `rate` é um parâmetro de `ByVal` porque `Calculate` não deve alterar seu valor.  
  
### Código  
 [!code-vb[VbVbcnProcedures#74](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Como alterar o valor de um argumento de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [Como proteger um argumento de procedimento contra alterações de valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Como forçar um argumento a ser passado por Valor](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)   
 [Passando argumentos por posição e nome](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)