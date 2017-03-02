---
title: Analisando outras cadeias de caracteres no .NET
description: Analisando outras cadeias de caracteres no .NET
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 67670b10-3df4-45ea-8908-5ba3f056887c
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: db80cc5f37e814f224ff76b14a906bb4d41064fb
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-other-strings-in-net"></a>Analisando outras cadeias de caracteres no .NET

Além das cadeias de caracteres numéricas e [DateTime](xref:System.DateTime), também é possível analisar cadeias de caracteres que representam os tipos [Char](xref:System.Char), [Boolean](xref:System.Boolean) e [Enum](xref:System.Enum) em tipos de dados.

## <a name="char"></a>Char

O método de análise estática associado ao tipo de dados [Char](xref:System.Char) é útil para converter uma cadeia de caracteres que contém um único caractere em seu valor Unicode. O exemplo de código a seguir analisa uma cadeia de caracteres em um caractere Unicode.

```csharp
string MyString1 = "A";
char MyChar = Char.Parse(MyString1);
// MyChar now contains a Unicode "A" character.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="boolean"></a>Boolean

O tipo de dados [Boolean](xref:System.Boolean) contém um método [Parse](xref:System.Boolean.Parse(System.String)) que pode ser usado para converter uma cadeia de caracteres que representa um valor `Boolean` em um tipo `Boolean` real. Esse método não diferencia maiúsculas de minúsculas e consegue analisar com êxito uma cadeia de caracteres que contém “True” ou “False”. O método `Parse` associado com o tipo `Boolean` também pode analisar cadeias de caracteres cercadas por espaços em branco. Se qualquer outra cadeia de caracteres for passada, será lançada uma [FormatException](xref:System.FormatException).

O exemplo de código a seguir usa o método `Parse` para converter uma cadeia de caracteres em um valor `Boolean`.

```csharp
string MyString2 = "True";
bool MyBool = bool.Parse(MyString2);
// MyBool now contains a True Boolean value.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="enumeration"></a>Enumeração

Você pode usar o método estático [Parse](xref:System.Enum.Parse(System.Type,System.String)) para inicializar um tipo de enumeração para o valor de uma cadeia de caracteres. Esse método aceita o tipo de enumeração que você estiver analisando, a cadeia de caracteres a analisar e um sinalizador `Boolean` opcional que indica se a análise diferencia maiúsculas de minúsculas ou não. A cadeia de caracteres que você está analisando pode conter diversos valores separados por vírgulas, que podem ser antecedidos ou seguidos por um ou mais espaços vazios (também chamados de espaços em branco). Quando a cadeia de caracteres contém diversos valores, o valor do objeto retornado é o valor de todos os valores especificados combinado com uma operação OR bit a bit.

O exemplo a seguir usa o método `Parse` para converter uma representação de cadeia de caracteres em um valor de enumeração. A enumeração [DayOfWeek](xref:System.DayOfWeek) é inicializada para quinta-feira de uma cadeia de caracteres.

```csharp
string MyString3 = "Thursday";
DayOfWeek MyDays = (DayOfWeek)Enum.Parse(typeof(DayOfWeek), MyString3);
Console.WriteLine(MyDays);
// The result is Thursday.
```

```vb
Dim MyString3 As String = "Thursday"
Dim MyDays As DayOfWeek = CType([Enum].Parse(GetType(DayOfWeek), MyString3), DayOfWeek)
Console.WriteLine("{0:G}", MyDays)
' The result is Thursday.
```

## <a name="see-also"></a>Consulte também

[Analisando cadeias de caracteres no .NET](parsing-strings.md)

[Tipos de formatação no .NET](formatting-types.md)

[Conversão de tipo no .NET](type-conversion.md)


