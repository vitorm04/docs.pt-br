---
title: "Diferen&#231;as entre par&#226;metros e argumentos (Visual Basic) | Microsoft Docs"
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
  - "argumentos [Visual Basic], e parâmetros"
  - "parâmetros, e argumentos"
  - "parâmetros, definição"
  - "argumentos de procedimento"
  - "parâmetros de procedimento"
  - "procedimentos, argumentos"
  - "procedimentos, parâmetros"
  - "código do Visual Basic, procedimentos"
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diferen&#231;as entre par&#226;metros e argumentos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Na maioria dos casos, um procedimento deve ter algumas informações sobre as circunstâncias em que foi chamado.  Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada.  Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando você o chama.  
  
 Para se comunicar essas informações para o procedimento, o procedimento define um  *parâmetro*, e o código de chamada passa um  *argumento* a este parâmetro.  Você pode considerar o parâmetro como um espaço de estacionamento e o argumento como um automóvel.  Assim como os automóveis diferentes podem estacionar em um espaço de estacionamento em momentos diferentes, o código de chamada pode passar um argumento diferente para o mesmo parâmetro toda vez que ele chama o procedimento.  
  
## Parâmetros  
 A  *parâmetro* representa um valor que o procedimento espera que você passe quando você chamá\-lo.  A declaração do procedimento define os seus parâmetros.  
  
 Quando você define uma `Function` ou `Sub` procedimento, você especifica um  *lista de parâmetros* em parênteses imediatamente após o nome do procedimento.  Para cada parâmetro, você especifica um nome, um tipo de dados e um mecanismo de passagem \([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)\).  Você também pode indicar que um parâmetro é opcional.  Isso significa que o código de chamada não tem um valor passado para ele.  
  
 O nome de cada parâmetro serve como um  *variável local* no procedimento.  Você usar o nome do parâmetro da mesma maneira que você use qualquer outra variável.  
  
## Argumentos  
 Um  *argumento* representa o valor que você passa para um parâmetro de procedimento, quando você chama o procedimento.  O código de chamada fornece os argumentos quando chama o procedimento.  
  
 Quando você chama um `Function` ou `Sub` procedimento, você incluir um  *lista de argumentos* em parênteses imediatamente após o nome do procedimento.  Cada argumento corresponde ao parâmetro na mesma posição na lista.  
  
 Em contraste com a definição do parâmetro, argumentos não têm nomes.  Cada argumento é uma expressão, que pode conter zero ou mais variáveis, constantes e literais.  O tipo de dados da expressão avaliada normalmente deve coincidir com o tipo de dados definido para o parâmetro correspondente e, em qualquer caso, ele deve ser convertido para o tipo de parâmetro.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como definir um parâmetro para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Procedimentos recursivos](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)