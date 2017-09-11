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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: db80cc5f37e814f224ff76b14a906bb4d41064fb
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="d664e-104">Analisando outras cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="d664e-104">Parsing other strings in .NET</span></span>

<span data-ttu-id="d664e-105">Além das cadeias de caracteres numéricas e [DateTime](xref:System.DateTime), também é possível analisar cadeias de caracteres que representam os tipos [Char](xref:System.Char), [Boolean](xref:System.Boolean) e [Enum](xref:System.Enum) em tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="d664e-105">In addition to numeric and [DateTime](xref:System.DateTime) strings, you can also parse strings that represent the types [Char](xref:System.Char), [Boolean](xref:System.Boolean), and [Enum](xref:System.Enum) into data types.</span></span>

## <a name="char"></a><span data-ttu-id="d664e-106">Char</span><span class="sxs-lookup"><span data-stu-id="d664e-106">Char</span></span>

<span data-ttu-id="d664e-107">O método de análise estática associado ao tipo de dados [Char](xref:System.Char) é útil para converter uma cadeia de caracteres que contém um único caractere em seu valor Unicode.</span><span class="sxs-lookup"><span data-stu-id="d664e-107">The static parse method associated with the [Char](xref:System.Char) data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="d664e-108">O exemplo de código a seguir analisa uma cadeia de caracteres em um caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="d664e-108">The following code example parses a string into a Unicode character.</span></span>

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

## <a name="boolean"></a><span data-ttu-id="d664e-109">Boolean</span><span class="sxs-lookup"><span data-stu-id="d664e-109">Boolean</span></span>

<span data-ttu-id="d664e-110">O tipo de dados [Boolean](xref:System.Boolean) contém um método [Parse](xref:System.Boolean.Parse(System.String)) que pode ser usado para converter uma cadeia de caracteres que representa um valor `Boolean` em um tipo `Boolean` real.</span><span class="sxs-lookup"><span data-stu-id="d664e-110">The [Boolean](xref:System.Boolean) data type contains a [Parse](xref:System.Boolean.Parse(System.String)) method that you can use to convert a string that represents a `Boolean` value into an actual `Boolean` type.</span></span> <span data-ttu-id="d664e-111">Esse método não diferencia maiúsculas de minúsculas e consegue analisar com êxito uma cadeia de caracteres que contém “True” ou “False”.</span><span class="sxs-lookup"><span data-stu-id="d664e-111">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="d664e-112">O método `Parse` associado com o tipo `Boolean` também pode analisar cadeias de caracteres cercadas por espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="d664e-112">The `Parse` method associated with the `Boolean` type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="d664e-113">Se qualquer outra cadeia de caracteres for passada, será lançada uma [FormatException](xref:System.FormatException).</span><span class="sxs-lookup"><span data-stu-id="d664e-113">If any other string is passed, a [FormatException](xref:System.FormatException) is thrown.</span></span>

<span data-ttu-id="d664e-114">O exemplo de código a seguir usa o método `Parse` para converter uma cadeia de caracteres em um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d664e-114">The following code example uses the `Parse` method to convert a string into a `Boolean` value.</span></span>

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

## <a name="enumeration"></a><span data-ttu-id="d664e-115">Enumeração</span><span class="sxs-lookup"><span data-stu-id="d664e-115">Enumeration</span></span>

<span data-ttu-id="d664e-116">Você pode usar o método estático [Parse](xref:System.Enum.Parse(System.Type,System.String)) para inicializar um tipo de enumeração para o valor de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d664e-116">You can use the static [Parse](xref:System.Enum.Parse(System.Type,System.String)) method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="d664e-117">Esse método aceita o tipo de enumeração que você estiver analisando, a cadeia de caracteres a analisar e um sinalizador `Boolean` opcional que indica se a análise diferencia maiúsculas de minúsculas ou não.</span><span class="sxs-lookup"><span data-stu-id="d664e-117">This method accepts the enumeration type you are parsing, the string to parse, and an optional `Boolean` flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="d664e-118">A cadeia de caracteres que você está analisando pode conter diversos valores separados por vírgulas, que podem ser antecedidos ou seguidos por um ou mais espaços vazios (também chamados de espaços em branco).</span><span class="sxs-lookup"><span data-stu-id="d664e-118">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="d664e-119">Quando a cadeia de caracteres contém diversos valores, o valor do objeto retornado é o valor de todos os valores especificados combinado com uma operação OR bit a bit.</span><span class="sxs-lookup"><span data-stu-id="d664e-119">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>

<span data-ttu-id="d664e-120">O exemplo a seguir usa o método `Parse` para converter uma representação de cadeia de caracteres em um valor de enumeração.</span><span class="sxs-lookup"><span data-stu-id="d664e-120">The following example uses the `Parse` method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="d664e-121">A enumeração [DayOfWeek](xref:System.DayOfWeek) é inicializada para quinta-feira de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d664e-121">The [DayOfWeek](xref:System.DayOfWeek) enumeration is initialized to Thursday from a string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d664e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d664e-122">See Also</span></span>

[<span data-ttu-id="d664e-123">Analisando cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="d664e-123">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="d664e-124">Tipos de formatação no .NET</span><span class="sxs-lookup"><span data-stu-id="d664e-124">Formatting types in .NET</span></span>](formatting-types.md)

[<span data-ttu-id="d664e-125">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="d664e-125">Type conversion in .NET</span></span>](type-conversion.md)


