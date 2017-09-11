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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 076e10e095b50cc96187f2ec13ade2365d83dad3
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="using-the-stringbuilder-class"></a><span data-ttu-id="3aa33-104">Usando a classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="3aa33-104">Using the StringBuilder class</span></span>

<span data-ttu-id="3aa33-105">O objeto [Cadeia de caracteres](xref:System.String) é imutável.</span><span class="sxs-lookup"><span data-stu-id="3aa33-105">The [String](xref:System.String) object is immutable.</span></span> <span data-ttu-id="3aa33-106">Sempre que você usa um dos métodos na classe [System.String](xref:System.String), você cria um novo objeto de cadeia de caracteres na memória, o que requer uma nova alocação de espaço para esse novo objeto.</span><span class="sxs-lookup"><span data-stu-id="3aa33-106">Every time you use one of the methods in the [System.String](xref:System.String) class, you create a new string object in memory, which requires a new allocation of space for that new object.</span></span> <span data-ttu-id="3aa33-107">Em situações em que você precisa realizar repetidas modificações em uma cadeia de caracteres, a sobrecarga associada à criação de um novo objeto [Cadeia de caracteres](xref:System.String) pode ser dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="3aa33-107">In situations where you need to perform repeated modifications to a string, the overhead associated with creating a new [String](xref:System.String) object can be costly.</span></span> <span data-ttu-id="3aa33-108">A classe [System.Text.StringBuilder](xref:System.Text.StringBuilder) pode ser usada quando você deseja modificar uma cadeia de caracteres sem criar um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="3aa33-108">The [System.Text.StringBuilder](xref:System.Text.StringBuilder) class can be used when you want to modify a string without creating a new object.</span></span> <span data-ttu-id="3aa33-109">Por exemplo, o uso da classe [StringBuilder](xref:System.Text.StringBuilder) pode melhorar o desempenho ao concatenar várias cadeias de caracteres em um loop.</span><span class="sxs-lookup"><span data-stu-id="3aa33-109">For example, using the [StringBuilder](xref:System.Text.StringBuilder) class can boost performance when concatenating many strings together in a loop.</span></span>

## <a name="importing-the-systemtext-namespace"></a><span data-ttu-id="3aa33-110">Importando o namespace System.Text</span><span class="sxs-lookup"><span data-stu-id="3aa33-110">Importing the System.Text Namespace</span></span>

<span data-ttu-id="3aa33-111">A classe [StringBuilder](xref:System.Text.StringBuilder) é encontrada no namespace [System.Text](xref:System.Text).</span><span class="sxs-lookup"><span data-stu-id="3aa33-111">The [StringBuilder](xref:System.Text.StringBuilder) class is found in the [System.Text](xref:System.Text) namespace.</span></span> <span data-ttu-id="3aa33-112">Para evitar ter que fornecer um nome de tipo totalmente qualificado em seu código, você pode importar o namespace [System.Text](xref:System.Text):</span><span class="sxs-lookup"><span data-stu-id="3aa33-112">To avoid having to provide a fully qualified type name in your code, you can import the [System.Text](xref:System.Text) namespace:</span></span> 

```csharp
using System;
using System.Text;
```

```vb
Imports System.Text
```

## <a name="instantiating-a-stringbuilder-object"></a><span data-ttu-id="3aa33-113">Criando uma instância de um objeto StringBuilder</span><span class="sxs-lookup"><span data-stu-id="3aa33-113">Instantiating a StringBuilder Object</span></span>

<span data-ttu-id="3aa33-114">Você pode criar uma nova instância da classe [StringBuilder](xref:System.Text.StringBuilder) inicializando sua variável com um dos métodos do construtor sobrecarregados, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3aa33-114">You can create a new instance of the [StringBuilder](xref:System.Text.StringBuilder) class by initializing your variable with one of the overloaded constructor methods, as illustrated in the following example.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
```

## <a name="setting-the-capacity-and-length"></a><span data-ttu-id="3aa33-115">Definindo a capacidade e o comprimento</span><span class="sxs-lookup"><span data-stu-id="3aa33-115">Setting the Capacity and Length</span></span>

<span data-ttu-id="3aa33-116">Embora o [StringBuilder](xref:System.Text.StringBuilder) seja um objeto dinâmico que permite que você expanda o número de caracteres na cadeia de caracteres que ele encapsula, você pode especificar um valor para o número máximo de caracteres que ele pode conter.</span><span class="sxs-lookup"><span data-stu-id="3aa33-116">Although the [StringBuilder](xref:System.Text.StringBuilder) is a dynamic object that allows you to expand the number of characters in the string that it encapsulates, you can specify a value for the maximum number of characters that it can hold.</span></span> <span data-ttu-id="3aa33-117">Esse valor é chamado de capacidade do objeto e não deve ser confundido com o comprimento da cadeia de caracteres que o [StringBuilder](xref:System.Text.StringBuilder) atual contém.</span><span class="sxs-lookup"><span data-stu-id="3aa33-117">This value is called the capacity of the object and should not be confused with the length of the string that the current [StringBuilder](xref:System.Text.StringBuilder) holds.</span></span> <span data-ttu-id="3aa33-118">Por exemplo, você pode criar uma nova instância da classe [StringBuilder](xref:System.Text.StringBuilder) com a cadeia de caracteres "Hello", que tem um comprimento de 5 caracteres e você pode especificar que o objeto tenha uma capacidade máxima de 25.</span><span class="sxs-lookup"><span data-stu-id="3aa33-118">For example, you might create a new instance of the [StringBuilder](xref:System.Text.StringBuilder) class with the string "Hello", which has a length of 5, and you might specify that the object has a maximum capacity of 25.</span></span> <span data-ttu-id="3aa33-119">Quando você modifica o [StringBuilder](xref:System.Text.StringBuilder), ele não realocará tamanho para si mesmo até que a capacidade seja atingida.</span><span class="sxs-lookup"><span data-stu-id="3aa33-119">When you modify the [StringBuilder](xref:System.Text.StringBuilder), it does not reallocate size for itself until the capacity is reached.</span></span> <span data-ttu-id="3aa33-120">Quando isso ocorre, o novo espaço é alocado automaticamente e a capacidade é dobrada.</span><span class="sxs-lookup"><span data-stu-id="3aa33-120">When this occurs, the new space is allocated automatically and the capacity is doubled.</span></span> <span data-ttu-id="3aa33-121">Você pode especificar a capacidade da classe [StringBuilder](xref:System.Text.StringBuilder) usando um dos construtores sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="3aa33-121">You can specify the capacity of the [StringBuilder](xref:System.Text.StringBuilder) class using one of the overloaded constructors.</span></span> <span data-ttu-id="3aa33-122">O exemplo a seguir especifica que o objeto `MyStringBuilder` pode ser expandido para um máximo de 25 espaços.</span><span class="sxs-lookup"><span data-stu-id="3aa33-122">The following example specifies that the `MyStringBuilder` object can be expanded to a maximum of 25 spaces.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!", 25);
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!", 25) 
```

<span data-ttu-id="3aa33-123">Além disso, você pode usar a propriedade [Capacidade](xref:System.Text.StringBuilder.Capacity) de leitura/gravação para definir o comprimento máximo de seu objeto.</span><span class="sxs-lookup"><span data-stu-id="3aa33-123">Additionally, you can use the read/write [Capacity](xref:System.Text.StringBuilder.Capacity) property to set the maximum length of your object.</span></span> <span data-ttu-id="3aa33-124">O exemplo a seguir usa a propriedade [Capacidade](xref:System.Text.StringBuilder.Capacity) para definir o comprimento máximo de objeto.</span><span class="sxs-lookup"><span data-stu-id="3aa33-124">The following example uses the [Capacity](xref:System.Text.StringBuilder.Capacity) property to define the maximum object length.</span></span>

```csharp
MyStringBuilder.Capacity = 25;
```

```vb
MyStringBuilder.Capacity = 25
```

<span data-ttu-id="3aa33-125">O método [EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) pode ser usado para verificar a capacidade do [StringBuilder](xref:System.Text.StringBuilder) atual.</span><span class="sxs-lookup"><span data-stu-id="3aa33-125">The [EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) method can be used to check the capacity of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="3aa33-126">Se a capacidade for maior que o valor transmitido, nenhuma alteração é feita; no entanto, se a capacidade for menor do que o valor transmitido, a capacidade atual é alterada para corresponder ao valor transmitido.</span><span class="sxs-lookup"><span data-stu-id="3aa33-126">If the capacity is greater than the passed value, no change is made; however, if the capacity is smaller than the passed value, the current capacity is changed to match the passed value.</span></span>

<span data-ttu-id="3aa33-127">A propriedade [Comprimento](xref:System.Text.StringBuilder.Length) também pode ser exibida ou definida.</span><span class="sxs-lookup"><span data-stu-id="3aa33-127">The [Length](xref:System.Text.StringBuilder.Length) property can also be viewed or set.</span></span> <span data-ttu-id="3aa33-128">Se você definir a propriedade [Comprimento](xref:System.Text.StringBuilder.Length) para um valor maior que a propriedade [Capacidade](xref:System.Text.StringBuilder.Capacity), a propriedade [Capacidade](xref:System.Text.StringBuilder.Capacity) será alterada automaticamente para o mesmo valor que a propriedade [Comprimento](xref:System.Text.StringBuilder.Length).</span><span class="sxs-lookup"><span data-stu-id="3aa33-128">If you set the [Length](xref:System.Text.StringBuilder.Length) property to a value that is greater than the [Capacity](xref:System.Text.StringBuilder.Capacity) property, the [Capacity](xref:System.Text.StringBuilder.Capacity) property is automatically changed to the same value as the [Length](xref:System.Text.StringBuilder.Length) property.</span></span> <span data-ttu-id="3aa33-129">Definir a propriedade [Comprimento](xref:System.Text.StringBuilder.Length) para um valor menor que o comprimento da cadeia de caracteres no [StringBuilder](xref:System.Text.StringBuilder) atual, diminui a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3aa33-129">Setting the [Length](xref:System.Text.StringBuilder.Length) property to a value that is less than the length of the string within the current [StringBuilder](xref:System.Text.StringBuilder) shortens the string.</span></span>

## <a name="modifying-the-stringbuilder-string"></a><span data-ttu-id="3aa33-130">Modificando a cadeia de caracteres do StringBuilder</span><span class="sxs-lookup"><span data-stu-id="3aa33-130">Modifying the StringBuilder String</span></span>

<span data-ttu-id="3aa33-131">A tabela a seguir lista os métodos que você pode usar para modificar o conteúdo de um [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="3aa33-131">The following table lists the methods you can use to modify the contents of a [StringBuilder](xref:System.Text.StringBuilder).</span></span>

<span data-ttu-id="3aa33-132">Nome do método</span><span class="sxs-lookup"><span data-stu-id="3aa33-132">Method name</span></span> | <span data-ttu-id="3aa33-133">Use</span><span class="sxs-lookup"><span data-stu-id="3aa33-133">Use</span></span>
----------- | ---
<span data-ttu-id="3aa33-134">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char))</span><span class="sxs-lookup"><span data-stu-id="3aa33-134">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char))</span></span> | <span data-ttu-id="3aa33-135">Acrescenta informações ao final do [StringBuilder](xref:System.Text.StringBuilder) atual.</span><span class="sxs-lookup"><span data-stu-id="3aa33-135">Appends information to the end of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="3aa33-136">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="3aa33-136">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span></span> | <span data-ttu-id="3aa33-137">Substitui um especificador de formato transmitido em uma cadeia de caracteres com texto formatado.</span><span class="sxs-lookup"><span data-stu-id="3aa33-137">Replaces a format specifier passed in a string with formatted text.</span></span>
<span data-ttu-id="3aa33-138">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char))</span><span class="sxs-lookup"><span data-stu-id="3aa33-138">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char))</span></span> | <span data-ttu-id="3aa33-139">Insere uma cadeia de caracteres ou um objeto no índice especificado do [StringBuilder](xref:System.Text.StringBuilder) atual.</span><span class="sxs-lookup"><span data-stu-id="3aa33-139">Inserts a string or object into the specified index of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="3aa33-140">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3aa33-140">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32))</span></span> | <span data-ttu-id="3aa33-141">Remove um número especificado de caracteres do [StringBuilder](xref:System.Text.StringBuilder) atual.</span><span class="sxs-lookup"><span data-stu-id="3aa33-141">Removes a specified number of characters from the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="3aa33-142">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char))</span><span class="sxs-lookup"><span data-stu-id="3aa33-142">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char))</span></span> | <span data-ttu-id="3aa33-143">Substitui um caractere especificado em um índice especificado.</span><span class="sxs-lookup"><span data-stu-id="3aa33-143">Replaces a specified character at a specified index.</span></span>

### <a name="append"></a><span data-ttu-id="3aa33-144">Acrescentar</span><span class="sxs-lookup"><span data-stu-id="3aa33-144">Append</span></span>

<span data-ttu-id="3aa33-145">O método [StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) pode ser usado para adicionar texto ou uma representação de cadeia de caracteres de um objeto ao final de uma cadeia de caracteres representada pelo [StringBuilder](xref:System.Text.StringBuilder) atual.</span><span class="sxs-lookup"><span data-stu-id="3aa33-145">The [StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) method can be used to add text or a string representation of an object to the end of a string represented by the current [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="3aa33-146">O exemplo a seguir inicializa um [StringBuilder](xref:System.Text.StringBuilder) para "Hello World" e, em seguida, acrescenta algum texto ao final do objeto.</span><span class="sxs-lookup"><span data-stu-id="3aa33-146">The following example initializes a [StringBuilder](xref:System.Text.StringBuilder) to "Hello World" and then appends some text to the end of the object.</span></span> <span data-ttu-id="3aa33-147">Espaço é alocado automaticamente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="3aa33-147">Space is allocated automatically as needed.</span></span>

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

### <a name="appendformat"></a><span data-ttu-id="3aa33-148">AppendFormat</span><span class="sxs-lookup"><span data-stu-id="3aa33-148">AppendFormat</span></span>

<span data-ttu-id="3aa33-149">O método [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) adiciona texto ao fim do objeto[StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="3aa33-149">The [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) method adds text to the end of the [StringBuilder](xref:System.Text.StringBuilder) object.</span></span> <span data-ttu-id="3aa33-150">Ele dá suporte ao recurso de formatação de composição (para obter mais informações, consulte [Formatação de composição](composite-format.md)) chamando a implementação [IFormattable](xref:System.IFormattable) do objeto ou objetos a serem formatados.</span><span class="sxs-lookup"><span data-stu-id="3aa33-150">It supports the composite formatting feature (for more information, see [Composite Formatting](composite-format.md)) by calling the [IFormattable](xref:System.IFormattable) implementation of the object or objects to be formatted.</span></span> <span data-ttu-id="3aa33-151">Portanto, aceita as cadeias de caracteres de formato padrão para valores numéricos, data e hora e enumeração, cadeias de caracteres de formato personalizado para valores numéricos e de data e hora e cadeias de caracteres de formato definidas para tipos personalizados.</span><span class="sxs-lookup"><span data-stu-id="3aa33-151">Therefore, it accepts the standard format strings for numeric, date and time, and enumeration values, the custom format strings for numeric and date and time values, and the format strings defined for custom types.</span></span> <span data-ttu-id="3aa33-152">(Para obter informações sobre a formatação, consulte [Formatando tipos](formatting-types.md).) Você pode usar esse método para personalizar o formato de variáveis e acrescentar esses valores a um [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="3aa33-152">(For information about formatting, see [Formatting Types](formatting-types.md).) You can use this method to customize the format of variables and append those values to a [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="3aa33-153">O exemplo a seguir usa o método AppendFormat para colocar um valor inteiro, formatado como um valor de moeda, no final de um objeto [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="3aa33-153">The following example uses the AppendFormat method to place an integer value formatted as a currency value at the end of a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="insert"></a><span data-ttu-id="3aa33-154">Inserir</span><span class="sxs-lookup"><span data-stu-id="3aa33-154">Insert</span></span>

<span data-ttu-id="3aa33-155">O método [StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) adiciona uma cadeia de caracteres ou um objeto a uma posição especificada no objeto [StringBuilder](xref:System.Text.StringBuilder) atual.</span><span class="sxs-lookup"><span data-stu-id="3aa33-155">The [StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) method adds a string or object to a specified position in the current [StringBuilder](xref:System.Text.StringBuilder) object.</span></span> <span data-ttu-id="3aa33-156">O exemplo a seguir usa esse método para inserir uma palavra na sexta posição de um objeto [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="3aa33-156">The following example uses this method to insert a word into the sixth position of a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="remove"></a><span data-ttu-id="3aa33-157">Remover</span><span class="sxs-lookup"><span data-stu-id="3aa33-157">Remove</span></span>

<span data-ttu-id="3aa33-158">Você pode usar o método [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) para remover um número especificado de caracteres do objeto [StringBuilder](xref:System.Text.StringBuilder) atual, começando em um índice com base zero especificado.</span><span class="sxs-lookup"><span data-stu-id="3aa33-158">You can use the [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) method to remove a specified number of characters from the current [StringBuilder](xref:System.Text.StringBuilder) object, beginning at a specified zero-based index.</span></span> <span data-ttu-id="3aa33-159">O exemplo a seguir usa o método [Remover](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) para reduzir um objeto [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="3aa33-159">The following example uses the [Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) method to shorten a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="replace"></a><span data-ttu-id="3aa33-160">Substituir</span><span class="sxs-lookup"><span data-stu-id="3aa33-160">Replace</span></span>

<span data-ttu-id="3aa33-161">O [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Substitui um caractere especificado em um índice especificado.</span><span class="sxs-lookup"><span data-stu-id="3aa33-161">The [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Replaces a specified character at a specified index.</span></span>
<span data-ttu-id="3aa33-162">método pode ser usado para substituir caracteres dentro do objeto [StringBuilder](xref:System.Text.StringBuilder) com outro caractere especificado.</span><span class="sxs-lookup"><span data-stu-id="3aa33-162">method can be used to replace characters within the [StringBuilder](xref:System.Text.StringBuilder) object with another specified character.</span></span> <span data-ttu-id="3aa33-163">O exemplo a seguir usa o [Substituir](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Substitui um caractere especificado em um índice especificado.</span><span class="sxs-lookup"><span data-stu-id="3aa33-163">The following example uses the [Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Replaces a specified character at a specified index.</span></span>
<span data-ttu-id="3aa33-164">método para pesquisar, em um objeto [StringBuilder](xref:System.Text.StringBuilder), todas as instâncias do caractere de ponto de exclamação (!) e substituí-los com o caractere de ponto de interrogação (?).</span><span class="sxs-lookup"><span data-stu-id="3aa33-164">method to search a [StringBuilder](xref:System.Text.StringBuilder) object for all instances of the exclamation point character (!) and replace them with the question mark character (?).</span></span>
 
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

## <a name="converting-a-stringbuilder-object-to-a-string"></a><span data-ttu-id="3aa33-165">Convertendo um objeto StringBuilder em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3aa33-165">Converting a StringBuilder Object to a String</span></span>

<span data-ttu-id="3aa33-166">Você deve converter o objeto [StringBuilder](xref:System.Text.StringBuilder) para um objeto [Cadeia de caracteres](xref:System.String) antes transmitir a cadeia de caracteres representada pelo objeto [StringBuilder](xref:System.Text.StringBuilder) para um método que tem um parâmetro [Cadeia de caracteres](xref:System.String) ou exibi-lo na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3aa33-166">You must convert the [StringBuilder](xref:System.Text.StringBuilder) object to a [String](xref:System.String) object before you can pass the string represented by the [StringBuilder](xref:System.Text.StringBuilder) object to a method that has a [String](xref:System.String) parameter or display it in the user interface.</span></span> <span data-ttu-id="3aa33-167">Você faz essa conversão chamando o método [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString).</span><span class="sxs-lookup"><span data-stu-id="3aa33-167">You do this conversion by calling the [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) method.</span></span> <span data-ttu-id="3aa33-168">O exemplo a seguir chama um número de métodos [StringBuilder](xref:System.Text.StringBuilder) e, em seguida, chama o método [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) para exibir a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3aa33-168">The following example calls a number of [StringBuilder](xref:System.Text.StringBuilder) methods and then calls the [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) method to display the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3aa33-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3aa33-169">See Also</span></span>

[<span data-ttu-id="3aa33-170">System.Text.StringBuilder</span><span class="sxs-lookup"><span data-stu-id="3aa33-170">System.Text.StringBuilder</span></span>](xref:System.Text.StringBuilder)

[<span data-ttu-id="3aa33-171">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="3aa33-171">Basic string operations</span></span>](basic-string-operations.md)

[<span data-ttu-id="3aa33-172">Formatando tipos</span><span class="sxs-lookup"><span data-stu-id="3aa33-172">Formatting types</span></span>](formatting-types.md)

