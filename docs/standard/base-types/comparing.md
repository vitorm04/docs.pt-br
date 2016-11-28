---
title: Comparando cadeias de caracteres
description: Comparando cadeias de caracteres
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 920ee5e8-3d61-4941-b5af-fc50eaee427c
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 2ad585bd5475cf39aeae5dadc9ce3864c501a205

---

# <a name="comparing-strings"></a>Comparando cadeias de caracteres

O .NET fornece vários métodos para comparar os valores de cadeias de caracteres. A tabela a seguir lista e descreve os métodos de comparação de valores.

Nome do método | Use
----------- | ---
[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) | Compara os valores das duas cadeias de caracteres. Retorna um valor inteiro.
[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) | Compara duas cadeias de caracteres sem considerar a cultura local. Retorna um valor inteiro.
[String.CompareTo](xref:System.String.CompareTo(System.String)) | Compara o objeto atual de cadeia de caracteres a outra cadeia de caracteres. Retorna um valor inteiro.
[String.StartsWith](xref:System.String.StartsWith(System.String)) | Determina se uma cadeia de caracteres começa com a cadeia de caracteres passada. Representa um valor Booliano.
[String.EndsWith](xref:System.String.CompareTo(System.String)) | Determina se uma cadeia de caracteres termina com a cadeia de caracteres passada. Representa um valor Booliano.
[String.Equals](xref:System.String.CompareTo(System.String)) | Determina se duas cadeias de caracteres são iguais. Representa um valor Booliano.
[String.IndexOf](xref:System.String.IndexOf(System.Char)) | Retorna a posição do índice de um caractere ou uma cadeia de caracteres, começando do início da cadeia de caracteres que você está examinando. Retorna um valor inteiro.
[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) | Retorna a posição do índice de um caractere ou uma cadeia de caracteres, começando do fim da cadeia de caracteres que você está examinando. Retorna um valor inteiro.

## <a name="compare"></a>Comparar

O método estático [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) fornece uma maneira completa de comparar duas cadeias de caracteres. Esse método é cultural. Você pode usar essa função para comparar duas cadeias de caracteres ou subcadeias de duas cadeias de caracteres. Além disso, sobrecargas são fornecidas para considerar ou ignorar a variação cultural ou de caso. A tabela a seguir mostra os três valores inteiros que esse método pode retornar. 

Valor retornado | Condição
------------ | ---------
Um inteiro negativo | A primeira cadeia de caracteres precede a segunda cadeia de caracteres na ordem de classificação ou a primeira cadeia de caracteres é `null`.
0 | A primeira cadeia de caracteres e a segunda cadeia de caracteres são iguais ou ambas são `null`.
Um número inteiro positivo ou 1 | A primeira cadeia de caracteres precede a segunda cadeia de caracteres na ordem de classificação ou a segunda cadeia de caracteres é nula.
 
> [!IMPORTANT]
> O método [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) destina-se principalmente para uso em ordenação ou classificação de cadeias de caracteres. Você não deve usar o método [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) para testar a igualdade (ou seja, para procurar explicitamente um valor retornado de 0 sem considerar se uma cadeia de caracteres é menor que ou maior que a outra). Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o método [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).

O exemplo a seguir usa o método [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) para determinar os valores relativos das duas cadeias de caracteres.

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.Compare(string1, "Hello World?"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.Compare(string1, "Hello World?"))
```

Este exemplo exibe `-1` no console.

## <a name="compareordinal"></a>CompareOrdinal

O método [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) compara dois objetos de cadeia de caracteres sem considerar a cultura local. Os valores de retorno desse método são idênticos aos valores retornados pelo método `Compare` na tabela anterior.

> [!IMPORTANT]
> O método [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) destina-se principalmente para uso em ordenação ou classificação de cadeias de caracteres. Você não deve usar o método [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) para testar a igualdade (ou seja, para procurar explicitamente um valor retornado de 0 sem considerar se uma cadeia de caracteres é menor ou maior que a outra). Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o método [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).

O exemplo a seguir usa o método `CompareOrdinal` para comparar os valores de duas cadeias de caracteres.

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"))
```

Este exemplo exibe `-32` no console.

## <a name="compareto"></a>CompareTo

O método [String.CompareTo](xref:System.String.CompareTo(System.String)) compara a cadeia de caracteres que o objeto atual de cadeia de caracteres encapsula com outro objeto ou cadeia de caracteres. Os valores de retorno desse método são idênticos aos valores retornados pelo método `String.Compare` na tabela anterior.

> [!IMPORTANT]
> O método [String.CompareTo](xref:System.String.CompareTo(System.String)) destina-se principalmente para uso em ordenação ou classificação de cadeias de caracteres. Você não deve usar o método [String.CompareTo](xref:System.String.CompareTo(System.String)) para testar a igualdade (ou seja, para procurar explicitamente um valor retornado de 0 sem considerar se uma cadeia de caracteres é menor ou maior que a outra). Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o método [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).

O exemplo a seguir usa o método `String.CompareTo` para comparar o objeto `string1` ao objeto `string2`.

```csharp
string string1 = "Hello World";
string string2 = "Hello World!";
int MyInt = string1.CompareTo(string2);
Console.WriteLine( MyInt );
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World!"
Dim MyInt As Integer = string1.CompareTo(string2)
Console.WriteLine(MyInt)
```

Este exemplo exibe `-1` no console.

## <a name="equals"></a>Igual a

O método [String.Equals](xref:System.String.CompareTo(System.String)) pode facilmente determinar se duas cadeias de caracteres são as mesmas. Esse método que diferencia maiúsculas de minúsculas retorna um valor Booliano `true` ou `false`. Ele pode ser usado de uma classe existente, conforme ilustrado no exemplo a seguir. O exemplo a seguir usa o método `Equals` para determinar se um objeto de cadeia de caracteres contém a frase "Hello World".

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.Equals("Hello World"));
```

```vb
Dim string1 As String = "Hello World"
Console.WriteLine(string1.Equals("Hello World"))
```

Este exemplo exibe `true` no console.

Esse método também pode ser usado como um método estático. O exemplo a seguir compara dois objetos de cadeia de caracteres usando um método estático.

```csharp
string string1 = "Hello World";
string string2 = "Hello World";
Console.WriteLine(String.Equals(string1, string2));
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World"
Console.WriteLine(String.Equals(string1, string2))
```

Este exemplo exibe `true` no console.

## <a name="startswith-and-endswith"></a>StartsWith e EndsWith

Você pode usar o método [String.StartsWith](xref:System.String.StartsWith(System.String)) para determinar se um objeto de cadeia de caracteres começa com os mesmos caracteres que englobam outra cadeia de caracteres. Esse método que diferencia maiúsculas de minúsculas retorna `true` se o objeto atual de cadeia de caracteres começa com a cadeia de caracteres passada e `false` se não existir. O exemplo a seguir usa esse método para determinar se um objeto de cadeia de caracteres começa com "Hello".

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.StartsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.StartsWith("Hello"))
```

Este exemplo exibe `true` no console.

O método [String.EndsWith](xref:System.String.CompareTo(System.String)) compara uma cadeia de caracteres passada com os caracteres que existem no final do objeto de cadeia de caracteres atual. Ele também retorna um valor Booliano. O exemplo a seguir verifica o fim de uma cadeia de caracteres usando o método `EndsWith`.

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.EndsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.EndsWith("Hello"))
```

Este exemplo exibe `false` no console.

## <a name="indexof-and-lastindexof"></a>IndexOf e LastIndexOf

Você pode usar o método [String.IndexOf](xref:System.String.IndexOf(System.Char)) para determinar a posição da primeira ocorrência de um determinado caractere dentro de uma cadeia de caracteres. Esse método que diferencia maiúsculas de minúsculas inicia a contagem do início de uma cadeia de caracteres e retorna a posição de um caractere passado usando um índice baseado em zero. Se o caractere não for encontrado, um valor de -1 será retornado.

O exemplo a seguir usa o método `IndexOf` para pesquisar a primeira ocorrência do caractere '`l`' em uma cadeia de caracteres.

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.IndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.IndexOf("l"))
```

Este exemplo exibe `2` no console.

O método [String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) é semelhante ao método `String.IndexOf`, exceto que ele retorna a posição da última ocorrência de um determinado caractere dentro de uma cadeia de caracteres. Ele diferencia maiúsculas de minúsculas e usa um índice baseado em zero. 

O exemplo a seguir usa o método `LastIndexOf` para pesquisar a última ocorrência do caractere '`l`' em uma cadeia de caracteres.

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.LastIndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.LastIndexOf("l"))
```

Este exemplo exibe `9` no console.

Os dois métodos são úteis quando usados em conjunto com o método [String.Remove](xref:System.String.Remove(System.Int32)). Você pode usar tanto o método `IndexOf` quanto o `LastIndexOf` para recuperar a posição de um caractere e, em seguida, fornecer essa posição para o `Remove method` para remover um caractere ou uma palavra que começa com esse caractere.

## <a name="see-also"></a>Consulte também

[Operações básicas de cadeias de caracteres](basic-string-operations.md)















<!--HONumber=Nov16_HO4-->


