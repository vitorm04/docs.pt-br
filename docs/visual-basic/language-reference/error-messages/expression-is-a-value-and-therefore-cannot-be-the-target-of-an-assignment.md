---
title: Expressão é um valor e, por isso, não pode ser o destino de uma atribuição
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: d5aae4d30abbf9ed2af260412352a5e0452e0dcc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513030"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Expressão é um valor e, por isso, não pode ser o destino de uma atribuição

Uma instrução tenta atribuir um valor a uma expressão. Você pode atribuir um valor somente a uma variável, propriedade ou elemento de matriz gravável em tempo de execução. O exemplo a seguir ilustra como esse erro pode ocorrer.

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

Exemplos semelhantes podem ser aplicados a propriedades e elementos de matriz.

**Acesso indireto.** O acesso indireto por meio de um tipo de valor também pode gerar esse erro. Considere o exemplo de código a seguir, que tenta definir o valor <xref:System.Drawing.Point> de acessando- <xref:System.Windows.Forms.Control.Location%2A>o indiretamente por meio de.

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

A última instrução do exemplo anterior falha porque ela cria apenas uma alocação temporária para a <xref:System.Drawing.Point> estrutura retornada <xref:System.Windows.Forms.Control.Location%2A> pela propriedade. Uma estrutura é um tipo de valor e a estrutura temporária não é mantida após a execução da instrução. O problema é resolvido declarando e usando uma variável <xref:System.Windows.Forms.Control.Location%2A>para, que cria uma alocação mais permanente para <xref:System.Drawing.Point> a estrutura. O exemplo a seguir mostra o código que pode substituir a última instrução do exemplo anterior.

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**ID do erro:** BC30068

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Se a instrução atribuir um valor a uma expressão, substitua a expressão por uma única variável, propriedade ou elemento de matriz gravável.

- Se a instrução fizer acesso indireto por meio de um tipo de valor (geralmente uma estrutura), crie uma variável para conter o tipo de valor.

- Atribua a estrutura apropriada (ou outro tipo de valor) à variável.

- Use a variável para acessar a propriedade para atribuir um valor a ela.

## <a name="see-also"></a>Consulte também

- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
- [Solução de problemas de Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
