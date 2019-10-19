---
title: A cláusula de identificadores requer uma variável WithEvents definida no tipo recipiente ou em um de seus tipos base
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 191415408f607d0ff768e50c41fa9b3c4405a688
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582822"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>A cláusula de identificadores requer uma variável WithEvents definida no tipo recipiente ou em um de seus tipos base

Você não forneceu uma variável `WithEvents` na sua cláusula `Handles`. A palavra-chave `Handles` no final de uma declaração de procedimento faz com que ele manipule eventos gerados por uma variável de objeto declarada usando a palavra-chave `WithEvents`.

**ID do erro:** BC30506

## <a name="to-correct-this-error"></a>Para corrigir este erro

Forneça a variável de `WithEvents` necessária.

## <a name="example"></a>Exemplo

No exemplo a seguir, Visual Basic gera `BC30506` de erro do compilador porque a palavra-chave [WithEvents](../modifiers/withevents.md) não é usada na definição da instância <xref:System.Timers.Timer?displayProperty=nameWithType>.

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

O exemplo a seguir é compilado com êxito porque a variável `_timer1` é definida com a palavra-chave `WithEvents`:

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
