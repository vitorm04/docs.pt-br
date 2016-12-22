---
title: "Express&#227;o &#233; um valor e, por isso, n&#227;o pode ser o destino de uma atribui&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30068"
  - "vbc30068"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30068"
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o &#233; um valor e, por isso, n&#227;o pode ser o destino de uma atribui&#231;&#227;o
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma instrução tenta atribuir um valor a uma expressão.  Você pode atribuir um valor somente a uma variável gravável, propriedade ou elemento de matriz em tempo de execução.  O exemplo a seguir ilustra como esse erro pode ocorrer.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Exemplos de semelhantes poderiam aplicar propriedades e os elementos da matriz.  
  
 **Acesso indireto.** Acesso indireto através de um tipo de valor também pode gerar esse erro.  Considere o seguinte exemplo de código que tenta definir o valor de <xref:System.Drawing.Point> , acessando\-indiretamente por meio <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 A última instrução do exemplo anterior falha porque ele cria apenas uma alocação temporária para o <xref:System.Drawing.Point> estrutura retornada pelo <xref:System.Windows.Forms.Control.Location%2A> propriedade.  Uma estrutura é um tipo de valor e a estrutura temporária não é mantida depois que a instrução é executada.  O problema for resolvido, declarando e usando uma variável para <xref:System.Windows.Forms.Control.Location%2A>, que cria uma alocação mais permanente para o <xref:System.Drawing.Point> estrutura.  O exemplo a seguir mostra o código que pode substituir a última instrução do exemplo anterior.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **Identificação do erro:**  BC30068  
  
### Para corrigir este erro  
  
-   Se a instrução atribui um valor a uma expressão, substitua a expressão com uma única variável gravável, uma propriedade ou um elemento de matriz.  
  
-   Se a instrução faz acesso indireto através de um tipo de valor \(geralmente uma estrutura\), crie uma variável para o tipo de valor.  
  
-   Atribua a estrutura apropriada \(ou outro tipo de valor\) à variável.  
  
-   Use a variável para acessar a propriedade para atribuir um valor ela.  
  
## Consulte também  
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Solucionando problemas de procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)