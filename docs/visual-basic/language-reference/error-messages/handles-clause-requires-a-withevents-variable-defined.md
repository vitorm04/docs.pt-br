---
title: A cláusula de identificadores requer uma variável WithEvents definida no tipo recipiente ou em um de seus tipos base
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 04c94d3d32660d1a186a9bb377c49a53e1451be6
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512742"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>A cláusula de identificadores requer uma variável WithEvents definida no tipo recipiente ou em um de seus tipos base
Você não forneceu uma `WithEvents` variável em sua `Handles` cláusula. A `Handles` palavra-chave no final de uma declaração de procedimento faz com que ele manipule eventos gerados por uma variável de `WithEvents` objeto declarada usando a palavra-chave.
  
 **ID do erro:** BC30506

## <a name="to-correct-this-error"></a>Para corrigir este erro
  
- Forneça a variável `WithEvents` necessária.
  
## <a name="example"></a>Exemplo

No exemplo a seguir, Visual Basic gera um erro `BC30506` de compilador porque a palavra-chave [WithEvents](../modifiers/withevents.md) não é usada na <xref:System.Timers.Timer?displayProperty=nameWithType> definição da instância.

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}
    
    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

O exemplo a seguir é compilado com êxito porque a `_timer1` variável é definida com a `WithEvents` palavra-chave:

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a>Consulte também

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
