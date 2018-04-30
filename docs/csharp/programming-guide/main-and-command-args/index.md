---
title: Main() e argumentos de linha de comando (Guia de Programação em C#)
ms.date: 08/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 75610174fdc91e4a29f17dc5563a7298c56a44e2
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="85656-102">Main() e argumentos de linha de comando (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="85656-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="85656-103">O método `Main` é o ponto de entrada de um aplicativo C#.</span><span class="sxs-lookup"><span data-stu-id="85656-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="85656-104">(Bibliotecas e serviços não exigem um método `Main` como um ponto de entrada.) Quando o aplicativo é iniciado, o método `Main` é o primeiro método invocado.</span><span class="sxs-lookup"><span data-stu-id="85656-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="85656-105">Pode haver apenas um ponto de entrada em um programa C#.</span><span class="sxs-lookup"><span data-stu-id="85656-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="85656-106">Se tiver mais de uma classe que tenha um `Main` método, você deverá compilar seu programa com a opção do compilador **/main** para especificar qual método `Main` será usado como ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="85656-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="85656-107">Para obter mais informações, consulte [/main (opções do compilador C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="85656-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a><span data-ttu-id="85656-108">Visão geral</span><span class="sxs-lookup"><span data-stu-id="85656-108">Overview</span></span>

- <span data-ttu-id="85656-109">O método `Main` é o ponto de entrada de um programa executável; é onde o controle do programa começa e termina.</span><span class="sxs-lookup"><span data-stu-id="85656-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="85656-110">`Main` é declarado dentro de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="85656-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="85656-111">O `Main` deve ser [estático](../../../csharp/language-reference/keywords/static.md) e não precisa ser [público](../../../csharp/language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="85656-111">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="85656-112">(No exemplo anterior, ele recebe o acesso padrão de [particular](../../../csharp/language-reference/keywords/private.md).) A classe delimitadora ou struct não deve ser estático.</span><span class="sxs-lookup"><span data-stu-id="85656-112">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="85656-113">O `Main` pode ter um tipo de retorno `void`, `int` ou, a partir do C# 7.1, `Task` ou `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="85656-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="85656-114">Se e somente se `Main` retornar um `Task` ou `Task<int>`, a declaração de `Main` pode incluir o modificador [`async`](../../language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="85656-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="85656-115">Observe que isso exclui especificamente um método `async void Main`.</span><span class="sxs-lookup"><span data-stu-id="85656-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="85656-116">O método `Main` pode ser declarado com ou sem um parâmetro `string[]` que contém os argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="85656-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="85656-117">Ao usar o Visual Studio para criar aplicativos do Windows, você pode adicionar o parâmetro manualmente ou usar a classe <xref:System.Environment> para obter os argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="85656-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="85656-118">Os parâmetros são lidos como argumentos de linha de comando indexados por zero.</span><span class="sxs-lookup"><span data-stu-id="85656-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="85656-119">Ao contrário de C e C++, o nome do programa não é tratado como o primeiro argumento de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="85656-119">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="85656-120">A adição dos tipos de retorno `async`, `Task` e `Task<int>` simplifica o código do programa quando os aplicativos do console precisam iniciar e realizar operações assíncronas `await` no `Main`.</span><span class="sxs-lookup"><span data-stu-id="85656-120">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="85656-121">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="85656-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="85656-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85656-122">See also</span></span>
[<span data-ttu-id="85656-123">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="85656-123">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
[<span data-ttu-id="85656-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="85656-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="85656-125">Métodos</span><span class="sxs-lookup"><span data-stu-id="85656-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
[<span data-ttu-id="85656-126">Por dentro de um programa em C#</span><span class="sxs-lookup"><span data-stu-id="85656-126">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
