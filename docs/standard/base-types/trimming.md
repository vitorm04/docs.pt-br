---
title: Cortando e removendo caracteres das cadeias de caracteres
description: Cortando e removendo caracteres das cadeias de caracteres
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 95d818bc-2661-43f6-adb8-13b53abf9682
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 6105861882c3bfd525a2d902fd2600f5da10417d

---

# <a name="trimming-and-removing-characters-from-strings"></a>Cortando e removendo caracteres das cadeias de caracteres

Se estiver analisando as palavras individuais de uma sentença, você poderá encontrar palavras com espaços em branco em ambas as extremidades da palavra. Nessa situação, você pode usar um dos métodos de corte na classe [System.String](https://docs.microsoft.com/dotnet/core/api/System.String) para remover qualquer número de espaços ou de outros caracteres de uma posição especificada na cadeia de caracteres. A tabela a seguir descreve os métodos de corte disponíveis.

Nome do método | Use
----------- | ---
[String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) | Remove os espaços em branco ou caracteres especificados em uma matriz de caracteres do início e do final de uma cadeia de caracteres.
[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) | Remove os caracteres especificados em uma matriz de caracteres do final de uma cadeia de caracteres.
[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) | Remove os caracteres especificados em uma matriz de caracteres do início de uma cadeia de caracteres.
[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) | Remove um número especificado de caracteres de uma posição de índice especificada em uma cadeia de caracteres.


## <a name="trim"></a>Trim

Você pode remover espaços em branco com facilidade de ambas as extremidades de uma cadeia de caracteres usando o método [String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim), conforme é mostrado no exemplo a seguir.

```csharp
string MyString = " Big   ";
Console.WriteLine("Hello{0}World!", MyString);
string TrimString = MyString.Trim();
Console.WriteLine("Hello{0}World!", TrimString);
//       The example displays the following output:
//             Hello Big   World!
//             HelloBigWorld!
```

```vb
Dim MyString As String = " Big   "
Console.WriteLine("Hello{0}World!", MyString)
Dim TrimString As String = MyString.Trim()
Console.WriteLine("Hello{0}World!", TrimString)
' The example displays the following output:
'       Hello Big   World!
'       HelloBigWorld!
```

Você também poderá remover os caracteres que especificar em uma matriz de caracteres do início e do final de uma cadeia de caracteres. O exemplo a seguir remove caracteres de espaço em branco, pontos e asteriscos.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String header = "* A Short String. *";
      Console.WriteLine(header);
      Console.WriteLine(header.Trim( new Char[] { ' ', '*', '.' } ));
   }
}
// The example displays the following output:
//       * A Short String. *
//       A Short String
```

```vb
Module Example
   Public Sub Main()
      Dim header As String = "* A Short String. *"
      Console.WriteLine(header)
      Console.WriteLine(header.Trim( { " "c, "*"c, "."c } ))
   End Sub
End Module
' The example displays the following output:
'       * A Short String. *
'       A Short String
```

## <a name="trimend"></a>TrimEnd

O método [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) remove os caracteres do final de uma cadeia de caracteres, criando um novo objeto de cadeia de caracteres. Uma matriz de caracteres é passada para este método para especificar os caracteres a seres removidos. A ordem dos elementos na matriz de caracteres não afeta a operação de corte. O corte é interrompido quando um caractere não especificado na matriz é encontrado.

O exemplo a seguir remove as últimas letras de uma cadeia de caracteres usando o método TrimEnd. Neste exemplo, as posições do caractere `'r'` e do caractere `'W'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa. Observe que este código remove a última palavra de `MyString` mais uma parte da primeira.

```csharp
string MyString = "Hello World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

Esse código exibe `He` no console.

O exemplo a seguir remove as últimas palavras de uma cadeia de caracteres usando o método [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])). Nesse código, há uma vírgula após a palavra `Hello` e, como a vírgula não está especificada na matriz de caracteres para cortar, o corte termina na vírgula.

```csharp
string MyString = "Hello, World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello, World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

Esse código exibe `Hello,` no console.

## <a name="trimstart"></a>TrimStart

O método [String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) é semelhante ao método [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])), exceto que ele cria uma nova cadeia de caracteres removendo caracteres do início de um objeto de cadeia de caracteres existente. Uma matriz de caracteres é passada para o método [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) para especificar os caracteres a serem removidos. Assim como acontece com o método [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])), a ordem dos elementos na matriz de caracteres não afeta a operação de corte. O corte é interrompido quando um caractere não especificado na matriz é encontrado.

O exemplo a seguir remove a primeira palavra de uma cadeia de caracteres. Neste exemplo, as posições do caractere `'l'` e do caractere `'H'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa.

```csharp
string MyString = "Hello World!";
char[] MyChar = {'e', 'H','l','o',' ' };
string NewString = MyString.TrimStart(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"e","H","l","o"," " }
Dim NewString As String = MyString.TrimStart(MyChar)
Console.WriteLine(NewString)
```

Esse código exibe `World!` no console.

## <a name="remove"></a>Remover

O método [String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) remove um número especificado de caracteres que começam em uma posição especificada em uma cadeia de caracteres existente. Este método assume um índice baseado em zero.

O exemplo a seguir remove dez caracteres de uma cadeia de caracteres começando na posição cinco de um índice baseado em zero da cadeia de caracteres.

```csharp
string MyString = "Hello Beautiful World!";
Console.WriteLine(MyString.Remove(5,10));
// The example displays the following output:
//         Hello World!  
```

```vb
Dim MyString As String = "Hello Beautiful World!"
Console.WriteLine(MyString.Remove(5,10))
' The example displays the following output:
'         Hello World!
```

Você também pode remover um caractere ou uma subcadeia de caracteres especificada de uma cadeia de caracteres chamando o método [String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) e especificando uma cadeia de caracteres vazia ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) como a substituição. O exemplo a seguir remove todas as vírgulas de uma cadeia de caracteres.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String phrase = "a cold, dark night";
      Console.WriteLine("Before: {0}", phrase);
      phrase = phrase.Replace(",", "");
      Console.WriteLine("After: {0}", phrase);
   }
}
// The example displays the following output:
//       Before: a cold, dark night
//       After: a cold dark night
```

```vb
Module Example
   Public Sub Main()
      Dim phrase As String = "a cold, dark night"
      Console.WriteLine("Before: {0}", phrase)
      phrase = phrase.Replace(",", "")
      Console.WriteLine("After: {0}", phrase)
   End Sub
End Module
' The example displays the following output:
'       Before: a cold, dark night
'       After: a cold dark night
```

## <a name="see-also"></a>Consulte também

[Operações básicas de cadeias de caracteres](basic-string-operations.md)




<!--HONumber=Nov16_HO3-->


