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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 793b5bc4b26967104459fa2559c6127bb82f3a9d
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="creating-new-strings"></a><span data-ttu-id="d8528-104">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d8528-104">Creating new strings</span></span>

<span data-ttu-id="d8528-105">O .NET permite que cadeias de caracteres sejam criadas usando atribuição simples e sobrecarrega um construtor de classe para dar suporte à criação de cadeias de caracteres usando um número de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="d8528-105">.NET  allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="d8528-106">O .NET também fornece vários métodos na classe [System.String](xref:System.String) que criam novos objetos de cadeia de caracteres combinando várias cadeias de caracteres, matrizes de cadeias de caracteres ou objetos.</span><span class="sxs-lookup"><span data-stu-id="d8528-106">.NET also provides several methods in the [System.String](xref:System.String) class that create new string objects by combining several strings, arrays of strings, or objects.</span></span> 

## <a name="creating-strings-using-assignment"></a><span data-ttu-id="d8528-107">Criando cadeias de caracteres usando atribuição</span><span class="sxs-lookup"><span data-stu-id="d8528-107">Creating Strings Using Assignment</span></span>

<span data-ttu-id="d8528-108">A maneira mais fácil para criar um novo objeto [String](xref:System.String) é simplesmente atribuir uma cadeia de caracteres literal a um objeto [String](xref:System.String).</span><span class="sxs-lookup"><span data-stu-id="d8528-108">The easiest way to create a new [String](xref:System.String) object is simply to assign a string literal to a [String](xref:System.String) object.</span></span> 

## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="d8528-109">Criando cadeias de caracteres usando um construtor de classe</span><span class="sxs-lookup"><span data-stu-id="d8528-109">Creating Strings Using a Class Constructor</span></span>

<span data-ttu-id="d8528-110">Você pode usar sobrecargas do construtor de classe [String](xref:System.String) para criar cadeias de caracteres de matrizes de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-110">You can use overloads of the [String](xref:System.String) class constructor to create strings from character arrays.</span></span> <span data-ttu-id="d8528-111">Você também pode criar uma nova cadeia de caracteres duplicando um caractere específico, m número de vezes especificado.</span><span class="sxs-lookup"><span data-stu-id="d8528-111">You can also create a new string by duplicating a particular character a specified number of times.</span></span> 

## <a name="methods-that-return-strings"></a><span data-ttu-id="d8528-112">Métodos que retornam cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d8528-112">Methods that Return Strings</span></span>

<span data-ttu-id="d8528-113">A tabela a seguir lista vários métodos úteis que retornam novos objetos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-113">The following table lists several useful methods that return new string objects.</span></span>

<span data-ttu-id="d8528-114">Nome do método</span><span class="sxs-lookup"><span data-stu-id="d8528-114">Method name</span></span> | <span data-ttu-id="d8528-115">Use</span><span class="sxs-lookup"><span data-stu-id="d8528-115">Use</span></span>
----------- | ---
<span data-ttu-id="d8528-116">[String.Format](xref:System.String.Format(System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="d8528-116">[String.Format](xref:System.String.Format(System.String,System.Object))</span></span> | <span data-ttu-id="d8528-117">Cria uma cadeia de caracteres formatada de um conjunto de objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="d8528-117">Builds a formatted string from a set of input objects.</span></span>
<span data-ttu-id="d8528-118">[String.Concat](xref:System.String.Concat(System.String,System.String))</span><span class="sxs-lookup"><span data-stu-id="d8528-118">[String.Concat](xref:System.String.Concat(System.String,System.String))</span></span> | <span data-ttu-id="d8528-119">Cria cadeias de caracteres de duas ou mais cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-119">Builds strings from two or more strings.</span></span>
<span data-ttu-id="d8528-120">[String.Join](xref:System.String.Join(System.String,System.String[]))</span><span class="sxs-lookup"><span data-stu-id="d8528-120">[String.Join](xref:System.String.Join(System.String,System.String[]))</span></span> |<span data-ttu-id="d8528-121">Cria uma nova cadeia de caracteres combinando uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-121">Builds a new string by combining an array of strings.</span></span>
<span data-ttu-id="d8528-122">[String.Insert](xref:System.String.Insert(System.Int32,System.String))</span><span class="sxs-lookup"><span data-stu-id="d8528-122">[String.Insert](xref:System.String.Insert(System.Int32,System.String))</span></span> | <span data-ttu-id="d8528-123">Cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres no índice especificado de uma cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="d8528-123">Builds a new string by inserting a string into the specified index of an existing string.</span></span>
<span data-ttu-id="d8528-124">[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="d8528-124">[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32))</span></span> | <span data-ttu-id="d8528-125">Copia caracteres especificados de uma cadeia de caracteres para uma posição especificada em uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-125">Copies specified characters in a string into a specified position in an array of characters.</span></span>

### <a name="format"></a><span data-ttu-id="d8528-126">Formatar</span><span class="sxs-lookup"><span data-stu-id="d8528-126">Format</span></span>

<span data-ttu-id="d8528-127">Você pode usar o método `String.Format` para criar cadeias de caracteres formatadas e concatenar cadeias de caracteres que representam vários objetos.</span><span class="sxs-lookup"><span data-stu-id="d8528-127">You can use the `String.Format` method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="d8528-128">Este método converte automaticamente qualquer objeto passado em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-128">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="d8528-129">Por exemplo, se seu aplicativo precisar exibir um valor [Int32](xref:System.Int32) e um valor [DateTime](xref:System.DateTime) para o usuário, você pode facilmente criar uma cadeia de caracteres para representar esses valores usando o método `Format`.</span><span class="sxs-lookup"><span data-stu-id="d8528-129">For example, if your application must display an [Int32](xref:System.Int32) value and a [DateTime](xref:System.DateTime) value to the user, you can easily construct a string to represent these values using the `Format` method.</span></span> <span data-ttu-id="d8528-130">Para obter informações sobre as convenções de formatação usadas com esse método, consulte a seção sobre [formatação de composição](composite-format.md).</span><span class="sxs-lookup"><span data-stu-id="d8528-130">For information about formatting conventions used with this method, see the section on [composite formatting](composite-format.md).</span></span>

<span data-ttu-id="d8528-131">O exemplo a seguir usa o método `Format` para criar uma cadeia de caracteres que usa uma variável de inteiro.</span><span class="sxs-lookup"><span data-stu-id="d8528-131">The following example uses the `Format` method to create a string that uses an integer variable.</span></span>

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

<span data-ttu-id="d8528-132">Neste exemplo, [DateTime.Now](xref:System.DateTime.Now) exibe a data e hora atuais da maneira especificada pela cultura associada ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="d8528-132">In this example, [DateTime.Now](xref:System.DateTime.Now) displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>

### <a name="concat"></a><span data-ttu-id="d8528-133">Concat</span><span class="sxs-lookup"><span data-stu-id="d8528-133">Concat</span></span>

<span data-ttu-id="d8528-134">O método `String.Concat` pode ser usado para criar facilmente um novo objeto de cadeia de caracteres de dois ou mais objetos existentes.</span><span class="sxs-lookup"><span data-stu-id="d8528-134">The `String.Concat` method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="d8528-135">Ele fornece uma maneira independente da linguagem para concatenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-135">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="d8528-136">Este método aceita qualquer classe que deriva de `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="d8528-136">This method accepts any class that derives from `System.Object`.</span></span> <span data-ttu-id="d8528-137">O exemplo a seguir cria uma cadeia de caracteres de dois objetos de cadeia de caracteres existentes e um caractere de separação.</span><span class="sxs-lookup"><span data-stu-id="d8528-137">The following example creates a string from two existing string objects and a separating character.</span></span>

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

### <a name="join"></a><span data-ttu-id="d8528-138">Join</span><span class="sxs-lookup"><span data-stu-id="d8528-138">Join</span></span>

<span data-ttu-id="d8528-139">O método `String.Join` cria uma nova cadeia de caracteres de uma matriz de cadeias de caracteres e uma cadeia de caracteres de separador.</span><span class="sxs-lookup"><span data-stu-id="d8528-139">The `String.Join` method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="d8528-140">Esse método é útil se você quiser concatenar várias cadeias de caracteres fazendo uma lista, talvez separada por vírgula.</span><span class="sxs-lookup"><span data-stu-id="d8528-140">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>

<span data-ttu-id="d8528-141">O exemplo a seguir usa um espaço para associar uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-141">The following example uses a space to bind a string array.</span></span>

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

### <a name="insert"></a><span data-ttu-id="d8528-142">Inserir</span><span class="sxs-lookup"><span data-stu-id="d8528-142">Insert</span></span>

<span data-ttu-id="d8528-143">O método `String.Insert` cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres em uma posição especificada em outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-143">The `String.Insert` method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="d8528-144">Este método usa um índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="d8528-144">This method uses a zero-based index.</span></span> <span data-ttu-id="d8528-145">O exemplo a seguir insere uma cadeia de caracteres na quinta posição do índice de `MyString` e cria uma nova cadeia de caracteres com esse valor.</span><span class="sxs-lookup"><span data-stu-id="d8528-145">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>

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

### <a name="copyto"></a><span data-ttu-id="d8528-146">CopyTo</span><span class="sxs-lookup"><span data-stu-id="d8528-146">CopyTo</span></span>

<span data-ttu-id="d8528-147">O método `String.CopyTo` copia partes de uma cadeia de caracteres em uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-147">The `String.CopyTo` method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="d8528-148">Você pode especificar o índice inicial da cadeia de caracteres e o número de caracteres a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="d8528-148">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="d8528-149">Este método usa o índice de origem, uma matriz de caracteres, o índice de destino e o número de caracteres a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="d8528-149">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="d8528-150">Todos os índices são baseados em zero.</span><span class="sxs-lookup"><span data-stu-id="d8528-150">All indexes are zero-based.</span></span>

<span data-ttu-id="d8528-151">O exemplo a seguir usa o método `CopyTo` para copiar os caracteres da palavra "Hello" de um objeto de cadeia de caracteres para a primeira posição de índice de uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8528-151">The following example uses the `CopyTo` method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d8528-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8528-152">See Also</span></span>

[<span data-ttu-id="d8528-153">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d8528-153">Basic string operations</span></span>](basic-string-operations.md)

[<span data-ttu-id="d8528-154">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="d8528-154">Composite formatting</span></span>](composite-format.md)


