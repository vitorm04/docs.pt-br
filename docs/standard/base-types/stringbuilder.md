---
title: Usando a classe StringBuilder
description: Usando a classe StringBuilder
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: f4f5d1c7-d84d-4867-810f-2708cd6de0da
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 076e10e095b50cc96187f2ec13ade2365d83dad3
ms.lasthandoff: 03/02/2017

---

# <a name="using-the-stringbuilder-class"></a>Usando a classe StringBuilder

O objeto [Cadeia de caracteres](xref:System.String) é imutável. Sempre que você usa um dos métodos na classe [System.String](xref:System.String), você cria um novo objeto de cadeia de caracteres na memória, o que requer uma nova alocação de espaço para esse novo objeto. Em situações em que você precisa realizar repetidas modificações em uma cadeia de caracteres, a sobrecarga associada à criação de um novo objeto [Cadeia de caracteres](xref:System.String) pode ser dispendiosa. A classe [System.Text.StringBuilder](xref:System.Text.StringBuilder) pode ser usada quando você deseja modificar uma cadeia de caracteres sem criar um novo objeto. Por exemplo, o uso da classe [StringBuilder](xref:System.Text.StringBuilder) pode melhorar o desempenho ao concatenar várias cadeias de caracteres em um loop.

## <a name="importing-the-systemtext-namespace"></a>Importando o namespace System.Text

A classe [StringBuilder](xref:System.Text.StringBuilder) é encontrada no namespace [System.Text](xref:System.Text). Para evitar ter que fornecer um nome de tipo totalmente qualificado em seu código, você pode importar o namespace [System.Text](xref:System.Text): 

```csharp
using System;
using System.Text;
```

```vb
Imports System.Text
```

## <a name="instantiating-a-stringbuilder-object"></a>Criando uma instância de um objeto StringBuilder

Você pode criar uma nova instância da classe [StringBuilder](xref:System.Text.StringBuilder) inicializando sua variável com um dos métodos do construtor sobrecarregados, conforme ilustrado no exemplo a seguir.

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
```

## <a name="setting-the-capacity-and-length"></a>Definindo a capacidade e o comprimento

Embora o [StringBuilder](xref:System.Text.StringBuilder) seja um objeto dinâmico que permite que você expanda o número de caracteres na cadeia de caracteres que ele encapsula, você pode especificar um valor para o número máximo de caracteres que ele pode conter. Esse valor é chamado de capacidade do objeto e não deve ser confundido com o comprimento da cadeia de caracteres que o [StringBuilder](xref:System.Text.StringBuilder) atual contém. Por exemplo, você pode criar uma nova instância da classe [StringBuilder](xref:System.Text.StringBuilder) com a cadeia de caracteres "Hello", que tem um comprimento de 5 caracteres e você pode especificar que o objeto tenha uma capacidade máxima de 25. Quando você modifica o [StringBuilder](xref:System.Text.StringBuilder), ele não realocará tamanho para si mesmo até que a capacidade seja atingida. Quando isso ocorre, o novo espaço é alocado automaticamente e a capacidade é dobrada. Você pode especificar a capacidade da classe [StringBuilder](xref:System.Text.StringBuilder) usando um dos construtores sobrecarregados. O exemplo a seguir especifica que o objeto `MyStringBuilder` pode ser expandido para um máximo de 25 espaços.

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!", 25);
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!", 25) 
```

Além disso, você pode usar a propriedade [Capacidade](xref:System.Text.StringBuilder.Capacity) de leitura/gravação para definir o comprimento máximo de seu objeto. O exemplo a seguir usa a propriedade [Capacidade](xref:System.Text.StringBuilder.Capacity) para definir o comprimento máximo de objeto.

```csharp
MyStringBuilder.Capacity = 25;
```

```vb
MyStringBuilder.Capacity = 25
```

O método [EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) pode ser usado para verificar a capacidade do [StringBuilder](xref:System.Text.StringBuilder) atual. Se a capacidade for maior que o valor transmitido, nenhuma alteração é feita; no entanto, se a capacidade for menor do que o valor transmitido, a capacidade atual é alterada para corresponder ao valor transmitido.

A propriedade [Comprimento](xref:System.Text.StringBuilder.Length) também pode ser exibida ou definida. Se você definir a propriedade [Comprimento](xref:System.Text.StringBuilder.Length) para um valor maior que a propriedade [Capacidade](xref:System.Text.StringBuilder.Capacity), a propriedade [Capacidade](xref:System.Text.StringBuilder.Capacity) será alterada automaticamente para o mesmo valor que a propriedade [Comprimento](xref:System.Text.StringBuilder.Length). Definir a propriedade [Comprimento](xref:System.Text.StringBuilder.Length) para um valor menor que o comprimento da cadeia de caracteres no [StringBuilder](xref:System.Text.StringBuilder) atual, diminui a cadeia de caracteres.

## <a name="modifying-the-stringbuilder-string"></a>Modificando a cadeia de caracteres do StringBuilder

A tabela a seguir lista os métodos que você pode usar para modificar o conteúdo de um [StringBuilder](xref:System.Text.StringBuilder).

Nome do método | Use
----------- | ---
[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) | Acrescenta informações ao final do [StringBuilder](xref:System.Text.StringBuilder) atual.
[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) | Substitui um especificador de formato transmitido em uma cadeia de caracteres com texto formatado.
[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) | Insere uma cadeia de caracteres ou um objeto no índice especificado do [StringBuilder](xref:System.Text.StringBuilder) atual.
[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) | Remove um número especificado de caracteres do [StringBuilder](xref:System.Text.StringBuilder) atual.
[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Substitui um caractere especificado em um índice especificado.

### <a name="append"></a>Acrescentar

O método [StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) pode ser usado para adicionar texto ou uma representação de cadeia de caracteres de um objeto ao final de uma cadeia de caracteres representada pelo [StringBuilder](xref:System.Text.StringBuilder) atual. O exemplo a seguir inicializa um [StringBuilder](xref:System.Text.StringBuilder) para "Hello World" e, em seguida, acrescenta algum texto ao final do objeto. Espaço é alocado automaticamente conforme necessário.

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Append(" What a beautiful day.");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World! What a beautiful day.
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Append(" What a beautiful day.")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World! What a beautiful day.
```

### <a name="appendformat"></a>AppendFormat

O método [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) adiciona texto ao fim do objeto[StringBuilder](xref:System.Text.StringBuilder). Ele dá suporte ao recurso de formatação de composição (para obter mais informações, consulte [Formatação de composição](composite-format.md)) chamando a implementação [IFormattable](xref:System.IFormattable) do objeto ou objetos a serem formatados. Portanto, aceita as cadeias de caracteres de formato padrão para valores numéricos, data e hora e enumeração, cadeias de caracteres de formato personalizado para valores numéricos e de data e hora e cadeias de caracteres de formato definidas para tipos personalizados. (Para obter informações sobre a formatação, consulte [Formatando tipos](formatting-types.md).) Você pode usar esse método para personalizar o formato de variáveis e acrescentar esses valores a um [StringBuilder](xref:System.Text.StringBuilder). O exemplo a seguir usa o método AppendFormat para colocar um valor inteiro, formatado como um valor de moeda, no final de um objeto [StringBuilder](xref:System.Text.StringBuilder).

```csharp
int MyInt = 25; 
StringBuilder MyStringBuilder = new StringBuilder("Your total is ");
MyStringBuilder.AppendFormat("{0:C} ", MyInt);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Your total is $25.00
```

```vb
Dim MyInt As Integer = 25
Dim MyStringBuilder As New StringBuilder("Your total is ")
MyStringBuilder.AppendFormat("{0:C} ", MyInt)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'     Your total is $25.00 
```

### <a name="insert"></a>Inserir

O método [StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) adiciona uma cadeia de caracteres ou um objeto a uma posição especificada no objeto [StringBuilder](xref:System.Text.StringBuilder) atual. O exemplo a seguir usa esse método para inserir uma palavra na sexta posição de um objeto [StringBuilder](xref:System.Text.StringBuilder).

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Insert(6,"Beautiful ");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello Beautiful World!
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Insert(6, "Beautiful ")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'      Hello Beautiful World!
```

### <a name="remove"></a>Remover

Você pode usar o método [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) para remover um número especificado de caracteres do objeto [StringBuilder](xref:System.Text.StringBuilder) atual, começando em um índice com base zero especificado. O exemplo a seguir usa o método [Remover](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) para reduzir um objeto [StringBuilder](xref:System.Text.StringBuilder).

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Remove(5,7);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Remove(5, 7)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello
```

### <a name="replace"></a>Substituir

O [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Substitui um caractere especificado em um índice especificado.
método pode ser usado para substituir caracteres dentro do objeto [StringBuilder](xref:System.Text.StringBuilder) com outro caractere especificado. O exemplo a seguir usa o [Substituir](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Substitui um caractere especificado em um índice especificado.
método para pesquisar, em um objeto [StringBuilder](xref:System.Text.StringBuilder), todas as instâncias do caractere de ponto de exclamação (!) e substituí-los com o caractere de ponto de interrogação (?).
 
 ```csharp
 StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Replace('!', '?');
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World?
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Replace("!"c, "?"c)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World?
```

## <a name="converting-a-stringbuilder-object-to-a-string"></a>Convertendo um objeto StringBuilder em uma cadeia de caracteres

Você deve converter o objeto [StringBuilder](xref:System.Text.StringBuilder) para um objeto [Cadeia de caracteres](xref:System.String) antes transmitir a cadeia de caracteres representada pelo objeto [StringBuilder](xref:System.Text.StringBuilder) para um método que tem um parâmetro [Cadeia de caracteres](xref:System.String) ou exibi-lo na interface do usuário. Você faz essa conversão chamando o método [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString). O exemplo a seguir chama um número de métodos [StringBuilder](xref:System.Text.StringBuilder) e, em seguida, chama o método [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) para exibir a cadeia de caracteres.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      StringBuilder sb = new StringBuilder();
      bool flag = true;
      string[] spellings = { "recieve", "receeve", "receive" };
      sb.AppendFormat("Which of the following spellings is {0}:", flag);
      sb.AppendLine();
      for (int ctr = 0; ctr <= spellings.GetUpperBound(0); ctr++) {
         sb.AppendFormat("   {0}. {1}", ctr, spellings[ctr]);
         sb.AppendLine();
      }
      sb.AppendLine();
      Console.WriteLine(sb.ToString());
   }
}
// The example displays the following output:
//       Which of the following spellings is True:
//          0. recieve
//          1. receeve
//          2. receive
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim sb As New StringBuilder()
      Dim flag As Boolean = True
      Dim spellings() As String = { "recieve", "receeve", "receive" }
      sb.AppendFormat("Which of the following spellings is {0}:", flag)
      sb.AppendLine()
      For ctr As Integer = 0 To spellings.GetUpperBound(0)
         sb.AppendFormat("   {0}. {1}", ctr, spellings(ctr))
         sb.AppendLine()
      Next
      sb.AppendLine()
      Console.WriteLine(sb.ToString())
   End Sub
End Module
' The example displays the following output:
'       Which of the following spellings is True:
'          0. recieve
'          1. receeve
'          2. receive
```

## <a name="see-also"></a>Consulte também

[System.Text.StringBuilder](xref:System.Text.StringBuilder)

[Operações básicas de cadeias de caracteres](basic-string-operations.md)

[Formatando tipos](formatting-types.md)

