---
title: Operador NameOf
description: Saiba como usar o operador NameOf no Visual Basic
ms.date: 10/27/2019
f1_keywords:
- NameOf
- vb.NameOf
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 0e72c4cb0c10113e53067ea4a743ca5ee77bcc95
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828897"
---
# <a name="nameof-operator---visual-basic"></a><span data-ttu-id="94635-103">Operador NameOf-Visual Basic</span><span class="sxs-lookup"><span data-stu-id="94635-103">NameOf operator - Visual Basic</span></span>

<span data-ttu-id="94635-104">O operador `NameOf` obtém o nome de uma variável, tipo ou membro como uma cadeia de caracteres constante:</span><span class="sxs-lookup"><span data-stu-id="94635-104">The `NameOf` operator obtains the name of a variable, type, or member as the string constant:</span></span>

```vb
Console.WriteLine(NameOf(System.Collections.Generic))  ' output: Generic
Console.WriteLine(NameOf(List(Of Integer)))  ' output: List
Console.WriteLine(NameOf(List(Of Integer).Count))  ' output: Count
Console.WriteLine(NameOf(List(Of Integer).Add))  ' output: Add

Dim numbers As New List(Of Integer) From { 1, 2, 3 }
Console.WriteLine(NameOf(numbers))  ' output: numbers
Console.WriteLine(NameOf(numbers.Count))  ' output: Count
Console.WriteLine(NameOf(numbers.Add))  ' output: Add
```

<span data-ttu-id="94635-105">Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="94635-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="94635-106">O operador `NameOf` é avaliado no tempo de compilação e não tem efeitos no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="94635-106">The `NameOf` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="94635-107">Você pode usar o operador `NameOf` para tornar o código de verificação de argumentos mais passível de manutenção:</span><span class="sxs-lookup"><span data-stu-id="94635-107">You can use the `NameOf` operator to make the argument-checking code more maintainable:</span></span>

```vb
Private _name As String

Public Property Name As String
    Get
        Return _name
    End Get
    Set
        If value Is Nothing Then
            Throw New ArgumentNullException(NameOf(value), $"{NameOf(name)} cannot be null.")
        End If
    End Set
End Property
```

<span data-ttu-id="94635-108">O `NameOf` operador está disponível no Visual Basic 14 e posterior.</span><span class="sxs-lookup"><span data-stu-id="94635-108">The `NameOf` operator is available in Visual Basic 14 and later.</span></span>

## <a name="see-also"></a><span data-ttu-id="94635-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94635-109">See also</span></span>

- [<span data-ttu-id="94635-110">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="94635-110">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="94635-111">Operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94635-111">Operators (Visual Basic)</span></span>](index.md)
