---
title: Expressão é um valor e, por isso, não pode ser o destino de uma atribuição
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: dd5618bd0533f885a6aef8229b2d8cb1bc34c237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590232"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Expressão é um valor e, por isso, não pode ser o destino de uma atribuição
Uma instrução tenta atribuir um valor a uma expressão. Você pode atribuir um valor apenas para uma variável gravável, propriedade ou elemento de matriz em tempo de execução. O exemplo a seguir ilustra como esse erro pode ocorrer.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Exemplos semelhantes podem aplicar a propriedades e os elementos da matriz.  
  
 **Acesso indireto.** Acesso indireto por meio de um tipo de valor também pode gerar esse erro. Considere o seguinte exemplo de código, que tenta definir o valor de <xref:System.Drawing.Point> acessando indiretamente por meio <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 A última instrução do exemplo anterior falhará porque ela cria somente uma alocação temporária para o <xref:System.Drawing.Point> estrutura retornada pelo <xref:System.Windows.Forms.Control.Location%2A> propriedade. Uma estrutura é um tipo de valor e a estrutura temporária não é retida depois que a instrução é executada. O problema seja resolvido declarando e usando uma variável para <xref:System.Windows.Forms.Control.Location%2A>, que cria uma alocação mais permanente para o <xref:System.Drawing.Point> estrutura. O exemplo a seguir mostra o código que pode substituir a última instrução do exemplo anterior.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **ID do erro:** BC30068  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se a instrução atribui um valor a uma expressão, substitua a expressão com uma única variável gravável, propriedade ou elemento de matriz.  
  
-   Se a instrução faz acesso indireto por meio de um tipo de valor (normalmente uma estrutura), crie uma variável para manter o tipo de valor.  
  
-   Atribua a estrutura apropriada (ou outro tipo de valor) à variável.  
  
-   Use a variável para acessar a propriedade para atribuir a ela um valor.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Solução de problemas de Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
