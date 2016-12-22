---
title: "Como criar um procedimento (Visual Basic) | Microsoft Docs"
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
  - "declarações de procedimento"
  - "procedimentos, sobre procedimentos"
  - "procedimentos, definindo"
  - "código do Visual Basic, procedimentos"
  - "código do Visual Basic, reutilizando"
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um procedimento (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você coloca um procedimento entre uma declaração inicial \(`Sub` ou `Function`\) e uma declaração final \(`End Sub` ou `End Function`\).  Todo o código do procedimento fica entre essas duas declarações.  
  
 Um procedimento não pode conter outro procedimento, então suas declarações inicial e final devem ficar fora de qualquer outro procedimento.  
  
 Se você tem código que executa a mesma tarefa em pontos diferentes, você pode escrever a tarefa uma única vez como um procedimento e então chamá\-lo de diferentes pontos do seu código.  
  
### Criar um procedimento que não retorna um valor.  
  
1.  Fora de qualquer outro procedimento, utilize uma declaração `Sub` seguida de uma declaração `End Sub`.  
  
2.  Na declaração `Sub`, siga a palava\-chave `Sub` do nome do procedimento, e, em seguida, da lista de parâmetros em parênteses.  
  
3.  Posicione as declarações de código do procedimento entre as declarações `Sub` e `End Sub`.  
  
### Para criar um crocedimento que retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma declaração `Function` seguida de uma declaração `End Function`.  
  
2.  Na declaração `Function`, depois da palavra\-chave `Function` coloque o nome do procedimento, a lista de parâmetros entre parênteses, e finalmente uma cláusula `As` especificando o tipo de dados do valor de retorno.  
  
3.  Posicione as declarações de código do procedimento entre as declarações `Function` e `End Function`.  
  
4.  Use uma declaração `Return` para retornar o valor para o código de chamada.  
  
### Para conectar seu novo procedimento com os blocos antigos e repetitivos de código  
  
1.  Garanta que você define o novo procedimento num lugar onde o código antigo tem acesso a ele.  
  
2.  No seu bloco de código repetitivo antigo, substitua as declarações que executam a tarefa repetitiva com uma declaração única que chama o procedimento `Sub` ou `Function`.  
  
3.  Se seu procedimento é uma `Function` que retorna um valor, garanta que sua declaração de chamada executa uma ação com o valor retornado, como armazená\-lo numa variável, ou então seu valor será perdido.  
  
## Exemplo  
 O procedimento `Function` a seguir calcula o maior lado, ou hipotenusa, de um triângulo retângulo, dados os valores dos outros dois lados.  
  
 [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedimentos recursivos](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programação orientada a objeto](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)