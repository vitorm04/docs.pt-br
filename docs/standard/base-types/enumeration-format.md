---
title: "Cadeias de caracteres de formato de enumeração"
description: "Cadeias de caracteres de formato de enumeração"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 4d581898-99bc-42c3-816c-d8238f45096f
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 9f5b60a75bf4b92b88d249be2f95f312ddb6909c

---

# <a name="enumeration-format-strings"></a>Cadeias de caracteres de formato de enumeração

Você pode usar o método [Enum.ToString](xref:System.Enum.ToString) para criar um novo objeto de cadeia de caracteres que representa o valor numérico, hexadecimal ou de cadeia de caracteres de um membro da enumeração. Esse método usa uma das cadeias de caracteres de formatação de enumeração para especificar o valor que você deseja que seja retornado.

As seções a seguir listam as cadeias de caracteres de formatação de enumeração e os valores que elas retornam. Esses especificadores de formato não diferenciam maiúsculas de minúsculas.

## <a name="the-g-or-g-format-strings"></a>Cadeias de caracteres de formato G ou g

As cadeias de caracteres no formato G ou g exibem a entrada de enumeração como um valor de cadeia de caracteres. Caso contrário, é exibido o valor inteiro da instância atual. Se a enumeração for definida com o atributo `Flags` definido, os valores de cadeia de caracteres de cada entrada válida são concatenados, separados por vírgulas. Se o atributo `Flags` não estiver definido, um valor inválido será exibido como uma entrada numérica. O exemplo a seguir ilustra o especificador de formato G.

```csharp
Console.WriteLine(ConsoleColor.Red.ToString("G"));         // Displays Red
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("G"));   // Displays Hidden, Archive
```

```vb
Console.WriteLine(ConsoleColor.Red.ToString("G"))           ' Displays Red
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("G"))     ' Displays Hidden, Archive
```

## <a name="the-f-or-f-format-strings"></a>Cadeias de caracteres de formato F ou f

As cadeias de caracteres de formato F ou f exibem a entrada de enumeração como um valor de cadeia de caracteres, se possível. Se o valor puder ser exibido totalmente como uma soma das entradas na enumeração (mesmo que o `Flags` atributo não esteja presente), os valores de cadeia de caracteres de cada entrada válida serão concatenados, separados por vírgulas. Se não puder ser determinado completamente pelas entradas de enumeração, o valor será formatado como valor inteiro. O exemplo a seguir ilustra o especificador de formato F.

```csharp
Console.WriteLine(ConsoleColor.Blue.ToString("F"));       // Displays Blue
FileAttributes attributes = FileAttributes.Hidden | 
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("F"));   // Displays Hidden, Archive
```

```vb
Console.WriteLine(ConsoleColor.Blue.ToString("F"))         ' Displays Blue
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("F"))     ' Displays Hidden, Archive
```

## <a name="the-d-or-d-format-strings"></a>Cadeias de caracteres de formato D ou d

As cadeias de caracteres de formato D ou d exibem a entrada de enumeração como um valor inteiro na representação mais curta possível. O exemplo a seguir ilustra o especificador de formato D.

```csharp
Console.WriteLine(ConsoleColor.Cyan.ToString("D"));         // Displays 11
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("D"));                // Displays 34
````

```vb
Console.WriteLine(ConsoleColor.Cyan.ToString("D"))           ' Displays 11
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("D"))                  ' Displays 34 
```

## <a name="the-x-or-x-format-strings"></a>Cadeias de caracteres de formato X ou x

As cadeias de caracteres de formato X ou x exibem a entrada de enumeração como um valor hexadecimal. O valor é representado com zeros no início, conforme necessário, para garantir tenha no mínimo oito dígitos de comprimento. O exemplo a seguir ilustra o especificador de formato X.

```csharp
Console.WriteLine(ConsoleColor.Cyan.ToString("X"));   // Displays 0000000B
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("X"));          // Displays 00000022
```

```vb
Console.WriteLine(ConsoleColor.Cyan.ToString("X"))     ' Displays 0000000B
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("X"))            ' Displays 00000022 
```

## <a name="example"></a>Exemplo

O exemplo a seguir define uma enumeração chamada `Colors`, que consiste em três entradas: `Red`, `Blue` e `Green`.

 ```csharp
 public enum Color {Red = 1, Blue = 2, Green = 3}
```

```vb
Public Enum Color
   Red = 1
   Blue = 2
   Green = 3
End Enum
```

Após a enumeração ser definida, uma instância pode ser declarada da seguinte maneira.

```csharp
Color myColor = Color.Green;
```

```vb
Dim myColor As Color = Color.Green
```

O método `Color.ToString(System.String)` pode, então, ser usado para exibir o valor da enumeração de diferentes maneiras, dependendo do especificador de formato passado para ele.

```csharp
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("G"));
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("F"));
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("D"));
Console.WriteLine("The value of myColor is 0x{0}.", 
                  myColor.ToString("X"));
// The example displays the following output to the console:
//       The value of myColor is Green.
//       The value of myColor is Green.
//       The value of myColor is 3.
//       The value of myColor is 0x00000003.
```

```vb
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("G"))
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("F"))
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("D"))
Console.WriteLine("The value of myColor is 0x{0}.", _
                  myColor.ToString("X"))
' The example displays the following output to the console:
'       The value of myColor is Green.
'       The value of myColor is Green.
'       The value of myColor is 3.
'       The value of myColor is 0x00000003. 
```

## <a name="see-also"></a>Consulte também

[Formatando tipos](formatting-types.md)




<!--HONumber=Nov16_HO5-->


