---
title: Preenchimento de cadeias de caracteres
description: Preenchimento de cadeias de caracteres
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 1c8b3b44-d370-49e1-90b5-64ac81c02ae91c8b3b44-d370-49e1-90b5-64ac81c02ae9
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: b6c5d4c8a35aebdfca88801118cdeba25c0a7e65

---

# <a name="padding-strings"></a>Preenchimento de cadeias de caracteres

Use um dos métodos [System.String](xref:System.String) a seguir para criar uma nova cadeia de caracteres que consista em uma cadeia de caracteres original preenchida com caracteres à esquerda ou à direita até um comprimento total especificado. O caractere de preenchimento pode ser espaços ou um caractere especificado e, consequentemente, parece estar alinhado à direita ou à esquerda.

Nome do método | Use
----------- | ---
[String.PadLeft](xref:System.String.PadLeft(System.Int32)) | Acrescenta uma cadeia de caracteres com caracteres à esquerda até um comprimento total especificado.
[String.PadRight](xref:System.String.PadRight(System.Int32)) | Acrescenta uma cadeia de caracteres com caracteres à direita até um comprimento total especificado.

## <a name="padleft"></a>PadLeft

O método [String.PadLeft](xref:System.String.PadLeft(System.Int32)) cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à esquerda suficientes para uma cadeia de caracteres original atingir um comprimento total especificado. O método [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) usa espaço em branco como caractere de preenchimento e o método [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) permite especificar seu próprio caractere de preenchimento.

O exemplo de código a seguir usa o método [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) para criar uma nova cadeia de caracteres com vinte caracteres de comprimento. O exemplo exibe “`--------Hello World!`” no console.

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadLeft(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadLeft(20, "-"c))
```

## <a name="padright"></a>PadRight

O método [String.PadRight](xref:System.String.PadRight(System.Int32)) cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à direita suficientes para uma cadeia de caracteres original atingir um comprimento total especificado. O método [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) usa espaço em branco como caractere de preenchimento e o método [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) permite especificar seu próprio caractere de preenchimento.

O exemplo de código a seguir usa o método [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) para criar uma nova cadeia de caracteres com vinte caracteres de comprimento. O exemplo exibe “`Hello World!--------`” no console.

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadRight(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadRight(20, "-"c))
```

## <a name="see-also"></a>Consulte também

[Operações básicas de cadeias de caracteres](basic-string-operations.md)




<!--HONumber=Nov16_HO3-->


