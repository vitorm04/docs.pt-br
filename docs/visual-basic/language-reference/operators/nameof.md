---
title: Operador NameOf
description: Saiba como usar o operador NameOf no Visual Basic
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: e7dd55bfd98b34449b9f1a35375198598f57b46f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347014"
---
# <a name="nameof-operator---visual-basic"></a>Operador NameOf-Visual Basic

O operador `NameOf` obtém o nome de uma variável, tipo ou membro como uma cadeia de caracteres constante:

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

Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

O operador `NameOf` é avaliado no tempo de compilação e não tem efeitos no tempo de execução.

Você pode usar o operador `NameOf` para tornar o código de verificação de argumentos mais passível de manutenção:

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

O operador `NameOf` está disponível no Visual Basic 14 e posterior.

## <a name="see-also"></a>Veja também

- [Referência da linguagem Visual Basic](../index.md)
- [Operadores (Visual Basic)](index.md)
