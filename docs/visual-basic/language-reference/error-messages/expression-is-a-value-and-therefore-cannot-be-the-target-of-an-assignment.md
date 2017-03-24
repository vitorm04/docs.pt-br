---
title: "Expressão é um valor e, portanto, não pode ser o destino de uma atribuição | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
dev_langs:
- VB
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 5789feb4f5b144d17464e006e019c13b5a756a19
ms.lasthandoff: 03/13/2017

---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Expressão é um valor e, por isso, não pode ser o destino de uma atribuição
Uma declaração tenta atribuir um valor a uma expressão. Você pode atribuir um valor apenas para uma variável gravável, uma propriedade ou um elemento da matriz em tempo de execução. O exemplo a seguir ilustra como esse erro pode ocorrer.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Exemplos semelhantes pode aplicar propriedades e elementos de matriz.  
  
 **Acesso indireto.** Acesso indireto através de um tipo de valor também pode gerar esse erro. Considere o seguinte exemplo de código, que tenta definir o valor de <xref:System.Drawing.Point>Acessando indiretamente por meio de <xref:System.Windows.Forms.Control.Location%2A>.</xref:System.Windows.Forms.Control.Location%2A> </xref:System.Drawing.Point>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 A última instrução do exemplo anterior falhará porque ela cria somente uma alocação temporária para o <xref:System.Drawing.Point>estrutura retornada pelo <xref:System.Windows.Forms.Control.Location%2A>propriedade.</xref:System.Windows.Forms.Control.Location%2A> </xref:System.Drawing.Point> Uma estrutura é um tipo de valor e a estrutura temporária não é mantida após a instrução é executada. O problema é resolvido ao declarar e usar uma variável para <xref:System.Windows.Forms.Control.Location%2A>, que cria uma alocação mais permanente para o <xref:System.Drawing.Point>estrutura.</xref:System.Drawing.Point> </xref:System.Windows.Forms.Control.Location%2A> O exemplo a seguir mostra o código que pode substituir a última instrução do exemplo anterior.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **ID do erro:** BC30068  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se a instrução atribui um valor a uma expressão, substitua a expressão com uma única variável gravável, uma propriedade ou um elemento de matriz.  
  
-   Se a instrução faz acesso indireto através de um tipo de valor (geralmente uma estrutura), crie uma variável para conter o tipo de valor.  
  
-   Atribua a estrutura apropriada (ou outro tipo de valor) à variável.  
  
-   Use a variável para acessar a propriedade para atribuir um valor ela.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Solução de problemas de Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
