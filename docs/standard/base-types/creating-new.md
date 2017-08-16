---
title: Criando novas cadeias de caracteres
description: Criando novas cadeias de caracteres
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 639397c7-e694-43e0-845b-1681c62bd9fd
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 793b5bc4b26967104459fa2559c6127bb82f3a9d
ms.lasthandoff: 03/02/2017

---

# <a name="creating-new-strings"></a>Criando novas cadeias de caracteres

O .NET permite que cadeias de caracteres sejam criadas usando atribuição simples e sobrecarrega um construtor de classe para dar suporte à criação de cadeias de caracteres usando um número de parâmetros diferentes. O .NET também fornece vários métodos na classe [System.String](xref:System.String) que criam novos objetos de cadeia de caracteres combinando várias cadeias de caracteres, matrizes de cadeias de caracteres ou objetos. 

## <a name="creating-strings-using-assignment"></a>Criando cadeias de caracteres usando atribuição

A maneira mais fácil para criar um novo objeto [String](xref:System.String) é simplesmente atribuir uma cadeia de caracteres literal a um objeto [String](xref:System.String). 

## <a name="creating-strings-using-a-class-constructor"></a>Criando cadeias de caracteres usando um construtor de classe

Você pode usar sobrecargas do construtor de classe [String](xref:System.String) para criar cadeias de caracteres de matrizes de caracteres. Você também pode criar uma nova cadeia de caracteres duplicando um caractere específico, m número de vezes especificado. 

## <a name="methods-that-return-strings"></a>Métodos que retornam cadeias de caracteres

A tabela a seguir lista vários métodos úteis que retornam novos objetos de cadeia de caracteres.

Nome do método | Use
----------- | ---
[String.Format](xref:System.String.Format(System.String,System.Object)) | Cria uma cadeia de caracteres formatada de um conjunto de objetos de entrada.
[String.Concat](xref:System.String.Concat(System.String,System.String)) | Cria cadeias de caracteres de duas ou mais cadeias de caracteres.
[String.Join](xref:System.String.Join(System.String,System.String[])) |Cria uma nova cadeia de caracteres combinando uma matriz de cadeias de caracteres.
[String.Insert](xref:System.String.Insert(System.Int32,System.String)) | Cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres no índice especificado de uma cadeia de caracteres existente.
[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32)) | Copia caracteres especificados de uma cadeia de caracteres para uma posição especificada em uma matriz de caracteres.

### <a name="format"></a>Formatar

Você pode usar o método `String.Format` para criar cadeias de caracteres formatadas e concatenar cadeias de caracteres que representam vários objetos. Este método converte automaticamente qualquer objeto passado em uma cadeia de caracteres. Por exemplo, se seu aplicativo precisar exibir um valor [Int32](xref:System.Int32) e um valor [DateTime](xref:System.DateTime) para o usuário, você pode facilmente criar uma cadeia de caracteres para representar esses valores usando o método `Format`. Para obter informações sobre as convenções de formatação usadas com esse método, consulte a seção sobre [formatação de composição](composite-format.md).

O exemplo a seguir usa o método `Format` para criar uma cadeia de caracteres que usa uma variável de inteiro.

```csharp
int numberOfFleas = 12;
string miscInfo = String.Format("Your dog has {0} fleas. " +
                                "It is time to get a flea collar. " + 
                                "The current universal date is: {1:u}.", 
                                numberOfFleas, DateTime.Now);
Console.WriteLine(miscInfo);
// The example displays the following output:
//       Your dog has 12 fleas. It is time to get a flea collar. 
//       The current universal date is: 2008-03-28 13:31:40Z.
```

```vb
Dim numberOfFleas As Integer = 12
Dim miscInfo As String = String.Format("Your dog has {0} fleas. " & _
                                       "It is time to get a flea collar. " & _ 
                                       "The current universal date is: {1:u}.", _ 
                                       numberOfFleas, Date.Now)
Console.WriteLine(miscInfo)
' The example displays the following output:
'       Your dog has 12 fleas. It is time to get a flea collar. 
'       The current universal date is: 2008-03-28 13:31:40Z.
```

Neste exemplo, [DateTime.Now](xref:System.DateTime.Now) exibe a data e hora atuais da maneira especificada pela cultura associada ao thread atual.

### <a name="concat"></a>Concat

O método `String.Concat` pode ser usado para criar facilmente um novo objeto de cadeia de caracteres de dois ou mais objetos existentes. Ele fornece uma maneira independente da linguagem para concatenar cadeias de caracteres. Este método aceita qualquer classe que deriva de `System.Object`. O exemplo a seguir cria uma cadeia de caracteres de dois objetos de cadeia de caracteres existentes e um caractere de separação.

```csharp
string helloString1 = "Hello";
string helloString2 = "World!";
Console.WriteLine(String.Concat(helloString1, ' ', helloString2));
// The example displays the following output:
//      Hello World!
```

```vb
Dim helloString1 As String = "Hello"
Dim helloString2 As String = "World!"
Console.WriteLine(String.Concat(helloString1, " "c, helloString2))
' The example displays the following output:
'      Hello World!
```

### <a name="join"></a>Join

O método `String.Join` cria uma nova cadeia de caracteres de uma matriz de cadeias de caracteres e uma cadeia de caracteres de separador. Esse método é útil se você quiser concatenar várias cadeias de caracteres fazendo uma lista, talvez separada por vírgula.

O exemplo a seguir usa um espaço para associar uma matriz de cadeias de caracteres.

```csharp
string[] words = {"Hello", "and", "welcome", "to", "my" , "world!"};
Console.WriteLine(String.Join(" ", words));
// The example displays the following output:
//      Hello and welcome to my world!
```

```vb
Dim words() As String = {"Hello", "and", "welcome", "to", "my" , "world!"}
Console.WriteLine(String.Join(" ", words))
' The example displays the following output:
'      Hello and welcome to my world!
```

### <a name="insert"></a>Inserir

O método `String.Insert` cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres em uma posição especificada em outra cadeia de caracteres. Este método usa um índice baseado em zero. O exemplo a seguir insere uma cadeia de caracteres na quinta posição do índice de `MyString` e cria uma nova cadeia de caracteres com esse valor.

```csharp
string sentence = "Once a time.";   
 Console.WriteLine(sentence.Insert(4, " upon"));
 // The example displays the following output:
 //      Once upon a time.
```

```vb
Dim sentence As String = "Once a time."   
 Console.WriteLine(sentence.Insert(4, " upon"))
 ' The example displays the 
```

### <a name="copyto"></a>CopyTo

O método `String.CopyTo` copia partes de uma cadeia de caracteres em uma matriz de caracteres. Você pode especificar o índice inicial da cadeia de caracteres e o número de caracteres a serem copiados. Este método usa o índice de origem, uma matriz de caracteres, o índice de destino e o número de caracteres a serem copiados. Todos os índices são baseados em zero.

O exemplo a seguir usa o método `CopyTo` para copiar os caracteres da palavra "Hello" de um objeto de cadeia de caracteres para a primeira posição de índice de uma matriz de caracteres.

```csharp
string greeting = "Hello World!";
char[] charArray = {'W','h','e','r','e'};
Console.WriteLine("The original character array: {0}", new string(charArray));
greeting.CopyTo(0, charArray,0 ,5);
Console.WriteLine("The new character array: {0}", new string(charArray));
// The example displays the following output:
//       The original character array: Where
//       The new character array: Hello
```

```vb
Dim greeting As String = "Hello World!"
Dim charArray() As Char = {"W"c, "h"c, "e"c, "r"c, "e"c}
Console.WriteLine("The original character array: {0}", New String(charArray))
greeting.CopyTo(0, charArray,0 ,5)
Console.WriteLine("The new character array: {0}", New String(charArray))
' The example displays the following output:
'       The original character array: Where
'       The new character array: Hello
```

## <a name="see-also"></a>Consulte também

[Operações básicas de cadeias de caracteres](basic-string-operations.md)

[Formatação de composição](composite-format.md)


