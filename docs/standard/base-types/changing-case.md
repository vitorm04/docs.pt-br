---
title: "Alterando a definição de maiúsculas e minúsculas"
description: "Alterando a definição de maiúsculas e minúsculas"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 646c5afd-8aec-4393-9c00-f68ad2580c68
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 023f40969095627242d3652add853eb999c30c4b
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="changing-case"></a><span data-ttu-id="5ad88-104">Alterando a definição de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="5ad88-104">Changing case</span></span>

<span data-ttu-id="5ad88-105">Se você gravar um aplicativo que aceita a inserção de informações por um usuário, talvez você nunca tenha certeza se ele ou ela usará maiúsculas ou minúsculas para inserir os dados.</span><span class="sxs-lookup"><span data-stu-id="5ad88-105">If you write an application that accepts input from a user, you can never be sure what case he or she will use to enter the data.</span></span> <span data-ttu-id="5ad88-106">Muitas vezes, você quer que as cadeias de caracteres tenham a grafia de maiúsculas e minúsculas consistente, especialmente se você estiver exibindo-as na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="5ad88-106">Often, you want strings to be cased consistently, particularly if you are displaying them in the user interface.</span></span> <span data-ttu-id="5ad88-107">A tabela a seguir descreve dois métodos de alteração de maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ad88-107">The following table describes two case-changing methods.</span></span>

<span data-ttu-id="5ad88-108">Nome do método</span><span class="sxs-lookup"><span data-stu-id="5ad88-108">Method name</span></span> | <span data-ttu-id="5ad88-109">Use</span><span class="sxs-lookup"><span data-stu-id="5ad88-109">Use</span></span>
----------- | ---
[<span data-ttu-id="5ad88-110">String.ToUpper</span><span class="sxs-lookup"><span data-stu-id="5ad88-110">String.ToUpper</span></span>](xref:System.String.ToUpper) | <span data-ttu-id="5ad88-111">Converte todos os caracteres em uma cadeia de caracteres para maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ad88-111">Converts all characters in a string to uppercase.</span></span>
[<span data-ttu-id="5ad88-112">String.ToLower</span><span class="sxs-lookup"><span data-stu-id="5ad88-112">String.ToLower</span></span>](xref:System.String.ToLower) | <span data-ttu-id="5ad88-113">Converte todos os caracteres em uma cadeia de caracteres para minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ad88-113">Converts all characters in a string to lowercase.</span></span>

> [!WARNING]  
> <span data-ttu-id="5ad88-114">Observe que os métodos `String.ToUpper` e `String.ToLower` não devem ser usados para converter cadeias de caracteres a fim de compará-las ou testá-las quanto à igualdade.</span><span class="sxs-lookup"><span data-stu-id="5ad88-114">Note that the `String.ToUpper` and `String.ToLower` methods should not be used to convert strings in order to compare them or test them for equality.</span></span> 

## <a name="comparing-strings-of-mixed-case"></a><span data-ttu-id="5ad88-115">Comparando cadeias de caracteres em maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="5ad88-115">Comparing strings of mixed case</span></span>

<span data-ttu-id="5ad88-116">Para comparar cadeias de caracteres em maiúsculas e minúsculas para determinar se eles são iguais, chame uma das sobrecargas do método [String](xref:System) `Equals` com um parâmetro *comparisonType* e forneça um valor [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) para o argumento *comparisonType*.</span><span class="sxs-lookup"><span data-stu-id="5ad88-116">To compare strings of mixed case to determine whether they are equal, their, call one of the overloads of the [String](xref:System) `Equals` method with a *comparisonType* parameter, and provide a value of either [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for the *comparisonType* argument.</span></span> 

<span data-ttu-id="5ad88-117">Para obter mais informações, consulte [Práticas recomendadas para o uso de cadeias de caracteres](best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="5ad88-117">For more information, see [Best Practices for Using Strings](best-practices.md).</span></span> 

## <a name="toupper"></a><span data-ttu-id="5ad88-118">ToUpper</span><span class="sxs-lookup"><span data-stu-id="5ad88-118">ToUpper</span></span>

<span data-ttu-id="5ad88-119">O método [String.ToUpper](xref:System.String.ToUpper) altera todos os caracteres em uma cadeia de caracteres para maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ad88-119">The [String.ToUpper](xref:System.String.ToUpper) method changes all characters in a string to uppercase.</span></span> <span data-ttu-id="5ad88-120">O exemplo a seguir converte a cadeia de caracteres "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="5ad88-120">The following example converts the string "Hello World!"</span></span> <span data-ttu-id="5ad88-121">de maiúsculas e minúsculas para maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ad88-121">from mixed case to uppercase.</span></span>

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToUpper());
// This example displays the following output:
//       HELLO WORLD!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToUpper())
' This example displays the following output:
'       HELLO WORLD!
```

## <a name="tolower"></a><span data-ttu-id="5ad88-122">ToLower</span><span class="sxs-lookup"><span data-stu-id="5ad88-122">ToLower</span></span>

<span data-ttu-id="5ad88-123">O método [String.ToLower](xref:System.String.ToLower) é semelhante ao método anterior, mas, em vez disso, ele converte todos os caracteres em uma cadeia de caracteres para minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ad88-123">The [String.ToLower](xref:System.String.ToLower) method is similar to the previous method, but instead converts all the characters in a string to lowercase.</span></span> <span data-ttu-id="5ad88-124">O exemplo a seguir converte a cadeia de caracteres "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="5ad88-124">The following example converts the string "Hello World!"</span></span> <span data-ttu-id="5ad88-125">para minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ad88-125">to lowercase.</span></span>

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToLower());
// This example displays the following output:
//       hello world!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToLower())
' This example displays the following output:
'       hello world!
```

## <a name="see-also"></a><span data-ttu-id="5ad88-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ad88-126">See Also</span></span>

[<span data-ttu-id="5ad88-127">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="5ad88-127">Basic string operations</span></span>](basic-string-operations.md)

