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
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="8b3eb-102">A cláusula de identificadores requer uma variável WithEvents definida no tipo recipiente ou em um de seus tipos base</span><span class="sxs-lookup"><span data-stu-id="8b3eb-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="8b3eb-103">Você não forneceu uma `WithEvents` variável em sua `Handles` cláusula.</span><span class="sxs-lookup"><span data-stu-id="8b3eb-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="8b3eb-104">A `Handles` palavra-chave no final de uma declaração de procedimento faz com que ele manipule eventos gerados por uma variável de `WithEvents` objeto declarada usando a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="8b3eb-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>
  
 <span data-ttu-id="8b3eb-105">**ID do erro:** BC30506</span><span class="sxs-lookup"><span data-stu-id="8b3eb-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8b3eb-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8b3eb-106">To correct this error</span></span>
  
- <span data-ttu-id="8b3eb-107">Forneça a variável `WithEvents` necessária.</span><span class="sxs-lookup"><span data-stu-id="8b3eb-107">Supply the necessary `WithEvents` variable.</span></span>
  
## <a name="example"></a><span data-ttu-id="8b3eb-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b3eb-108">Example</span></span>

<span data-ttu-id="8b3eb-109">No exemplo a seguir, Visual Basic gera um erro `BC30506` de compilador porque a palavra-chave [WithEvents](../modifiers/withevents.md) não é usada na <xref:System.Timers.Timer?displayProperty=nameWithType> definição da instância.</span><span class="sxs-lookup"><span data-stu-id="8b3eb-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

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

<span data-ttu-id="8b3eb-110">O exemplo a seguir é compilado com êxito porque a `_timer1` variável é definida com a `WithEvents` palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="8b3eb-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8b3eb-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b3eb-111">See also</span></span>

- [<span data-ttu-id="8b3eb-112">Handles</span><span class="sxs-lookup"><span data-stu-id="8b3eb-112">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
