---
title: Preenchimento de cadeias de caracteres
description: Preenchimento de cadeias de caracteres
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1c8b3b44-d370-49e1-90b5-64ac81c02ae91c8b3b44-d370-49e1-90b5-64ac81c02ae9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: bc3cc9028b232cc2ba6ca3130c4bdb261c4a0a42
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="padding-strings"></a><span data-ttu-id="d8916-104">Preenchimento de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d8916-104">Padding strings</span></span>

<span data-ttu-id="d8916-105">Use um dos métodos [System.String](xref:System.String) a seguir para criar uma nova cadeia de caracteres que consista em uma cadeia de caracteres original preenchida com caracteres à esquerda ou à direita até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="d8916-105">Use one of the following [System.String](xref:System.String) methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="d8916-106">O caractere de preenchimento pode ser espaços ou um caractere especificado e, consequentemente, parece estar alinhado à direita ou à esquerda.</span><span class="sxs-lookup"><span data-stu-id="d8916-106">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>

<span data-ttu-id="d8916-107">Nome do método</span><span class="sxs-lookup"><span data-stu-id="d8916-107">Method name</span></span> | <span data-ttu-id="d8916-108">Use</span><span class="sxs-lookup"><span data-stu-id="d8916-108">Use</span></span>
----------- | ---
<span data-ttu-id="d8916-109">[String.PadLeft](xref:System.String.PadLeft(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="d8916-109">[String.PadLeft](xref:System.String.PadLeft(System.Int32))</span></span> | <span data-ttu-id="d8916-110">Acrescenta uma cadeia de caracteres com caracteres à esquerda até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="d8916-110">Pads a string with leading characters to a specified total length.</span></span>
<span data-ttu-id="d8916-111">[String.PadRight](xref:System.String.PadRight(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="d8916-111">[String.PadRight](xref:System.String.PadRight(System.Int32))</span></span> | <span data-ttu-id="d8916-112">Acrescenta uma cadeia de caracteres com caracteres à direita até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="d8916-112">Pads a string with trailing characters to a specified total length.</span></span>

## <a name="padleft"></a><span data-ttu-id="d8916-113">PadLeft</span><span class="sxs-lookup"><span data-stu-id="d8916-113">PadLeft</span></span>

<span data-ttu-id="d8916-114">O método [String.PadLeft](xref:System.String.PadLeft(System.Int32)) cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à esquerda suficientes para uma cadeia de caracteres original atingir um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="d8916-114">The [String.PadLeft](xref:System.String.PadLeft(System.Int32)) method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d8916-115">O método [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) usa espaço em branco como caractere de preenchimento e o método [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) permite especificar seu próprio caractere de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="d8916-115">The [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) method uses white space as the padding character and the [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) method enables you to specify your own padding character.</span></span>

<span data-ttu-id="d8916-116">O exemplo de código a seguir usa o método [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) para criar uma nova cadeia de caracteres com vinte caracteres de comprimento.</span><span class="sxs-lookup"><span data-stu-id="d8916-116">The following code example uses the [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d8916-117">O exemplo exibe “`--------Hello World!`” no console.</span><span class="sxs-lookup"><span data-stu-id="d8916-117">The example displays "`--------Hello World!`" to the console.</span></span>

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadLeft(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadLeft(20, "-"c))
```

## <a name="padright"></a><span data-ttu-id="d8916-118">PadRight</span><span class="sxs-lookup"><span data-stu-id="d8916-118">PadRight</span></span>

<span data-ttu-id="d8916-119">O método [String.PadRight](xref:System.String.PadRight(System.Int32)) cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à direita suficientes para uma cadeia de caracteres original atingir um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="d8916-119">The [String.PadRight](xref:System.String.PadRight(System.Int32)) method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d8916-120">O método [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) usa espaço em branco como caractere de preenchimento e o método [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) permite especificar seu próprio caractere de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="d8916-120">The [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) method uses white space as the padding character and the [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) method enables you to specify your own padding character.</span></span>

<span data-ttu-id="d8916-121">O exemplo de código a seguir usa o método [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) para criar uma nova cadeia de caracteres com vinte caracteres de comprimento.</span><span class="sxs-lookup"><span data-stu-id="d8916-121">The following code example uses the [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d8916-122">O exemplo exibe “`Hello World!--------`” no console.</span><span class="sxs-lookup"><span data-stu-id="d8916-122">The example displays "`Hello World!--------`" to the console.</span></span>

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadRight(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadRight(20, "-"c))
```

## <a name="see-also"></a><span data-ttu-id="d8916-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8916-123">See Also</span></span>

[<span data-ttu-id="d8916-124">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d8916-124">Basic string operations</span></span>](basic-string-operations.md)


