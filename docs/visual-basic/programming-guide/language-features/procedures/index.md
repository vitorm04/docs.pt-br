---
title: "Procedimentos no Visual Basic | Microsoft Docs"
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
  - "procedimentos"
  - "procedimentos, código estruturado"
  - "procedimentos, tipos de"
  - "código estruturado, procedimentos"
  - "código do Visual Basic, procedimentos"
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedimentos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um *procedimento* é um bloco de declarações [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cercadas por uma declaração \(`Function`,`Sub`,`Operator`,`Get`,`Set`\) e uma declaração `End` correspondente.  Todas as declarações executáveis em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] devem estar no interior de algum procedimento.  
  
## Chamando um Procedimento  
 Você invoca um procedimento de algum outro lugar no código.  Isso é conhecido como uma *chamada de procedimento*.  Quando o procedimento termina de executar, ele retorna o controle para o código que o invocou, que é conhecido como *código de chamada*.  O código de chamada é uma declaração, ou uma expressão no interior de uma declaração, que especifica o procedimento pelo nome e o transfere o controle.  
  
## Retornando a partir de um Procedimento.  
 Um procedimento retorna o controle para o código de chamada quando ele termina de executar.  Para fazê\-lo, pode\-se usar um [Instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md), a declaração [Instrução Exit](../../../../visual-basic/language-reference/statements/exit-statement.md) apropriada para o procedimento, o a declaração [Instrução End \<keyword\>](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) de procedimento.  O controle é então passado para o código de chamada seguindo o ponto de chamada do procedimento.  
  
-   Com uma declaração `Return`. o controle retorna imediatamente para o código de chamada.  Declarações após a declaração `Return` não são executadas.  Você pode ter mais de uma declaração `Return` no mesmo preocedimento.  
  
-   Com uma declaração `Exit Sub` ou `Exit Function`. o controle retorna imediatamente para o código de chamada.  Declarações após a declaração `Exit` não são executadas.  Você pode ter mais de uma declaração `Exit` no mesmo procedimento, e você pode mixar as declarações `Return` e `Exit` no mesmo procedimento.  
  
-   Se um procedimento não tem declarações `Return` ou `Exit`, conclui\-se com uma declaração `End Sub` ou `End Function`, declaração `End Get` ou `End Set` seguindo a última declaração do corpo do procedimento.  A declaração `End`. retorna imediatamente o controle para o código de chamada.  Você pode ter apenas uma declaração `End` em um procedimento.  
  
## Parâmetros e Argumentos  
 Na maioria dos casos, um procedimento precisa operar em diferentes dados cada vez que é chamado.  Você pode passar essa informação para o procedimento como parte da chamada de procedimento.  O procedimento define zero ou mais *parâmetros*, cada um representando um valor que se espera que seja passado.  Correspondendo a cada parâmetro na definição de procedimento há um *argumento* na chamada de procedimento.  Um argumento representa o valor que você passa para o parâmetro correspondente em uma dada chamada de procedimento.  
  
## Tipos de Procedimentos  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]usa vários tipos de procedimentos:  
  
-   [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) realiza ações mas não retorna um valor para o código de chamada.  
  
-   Procedimentos de tratamento de exceção são procedimentos `Sub` que executam em resposta a um evento lançado por ação do usuário ou por uma ocorrência em um programa.  
  
-   [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) retorna um valor para o código de chamada.  Eles podem realizar outras ações antes de retornar.  
  
-   [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) retorna e atribui valores de propriedades em objetos ou módulos.  
  
-   [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)Defina o comportamento de um operador padrão quando um ou ambos dos operandos for uma recém\-definidas classe ou estrutura.  
  
-   [Procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) define um ou mais *parâmetros de tipo* além de seus parâmetros normais, de tal forma que o código de chamada pode passar tipos de dado específicos cada vez que uma chamada é feita.  
  
## Procedimentos e Código Estruturado  
 Cada linha de código executável em seu aplicativo deve estar no interior de algum procedimento, tal como`Main`,`calculate`,ou`Button1_Click`.  Se você subdividir procedimentos maiores em procedimentos menores, sua aplicação se torna mais legível.  
  
 Procedimentos são úteis para realizar tarefas compartilhadas ou repetidas, tais como cálculos frequentemente usados, manipulação e controle de texto, e operações de banco de dados.  Você pode chamar um procedimento de vários lugar diferentes em seu código, sendo assim você pode usar procedimentos como blocos de construção para seu aplicativo  
  
 Estruturar seu código com procedimentos lhe traz os seguintes benefícios:  
  
-   Procedimentos lhe permitem dividir seus programas em unidades lógicas discretas.  Você pode depurar unidades separadas mais facilmente do que depurar um programa inteiro sem procedimentos.  
  
-   Depois de desenvolver procedimentos para uso em um programa, você pode usá\-los em outros programas, frequentemente com pouca ou nenhuma alteração.  Isso ajuda a evitar duplicação de código.  
  
## Consulte também  
 [Como criar um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedimentos recursivos](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)