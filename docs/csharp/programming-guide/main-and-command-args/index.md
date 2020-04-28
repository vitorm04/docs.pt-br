---
title: Main() e argumentos de linha de comando – Guia de Programação em C#
ms.date: 08/02/2017
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
ms.openlocfilehash: 190216b01ea416aedbca270a6d7a5acbf0c2e797
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200113"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="f5115-102">Main() e argumentos de linha de comando (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f5115-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="f5115-103">O método `Main` é o ponto de entrada de um aplicativo C#.</span><span class="sxs-lookup"><span data-stu-id="f5115-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="f5115-104">(Bibliotecas e serviços não exigem um `Main` método como um ponto de entrada.) Quando o aplicativo é iniciado, o `Main` método é o primeiro método que é invocado.</span><span class="sxs-lookup"><span data-stu-id="f5115-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="f5115-105">Pode haver apenas um ponto de entrada em um programa C#.</span><span class="sxs-lookup"><span data-stu-id="f5115-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="f5115-106">Se tiver mais de uma classe que tenha um `Main` método, você deverá compilar seu programa com a opção do compilador **/main** para especificar qual método `Main` será usado como ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="f5115-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="f5115-107">Para obter mais informações, consulte [-Main (opções do compilador C#)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f5115-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="f5115-108">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f5115-108">Overview</span></span>

- <span data-ttu-id="f5115-109">O método `Main` é o ponto de entrada de um programa executável; é onde o controle do programa começa e termina.</span><span class="sxs-lookup"><span data-stu-id="f5115-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="f5115-110">`Main` é declarado dentro de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="f5115-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="f5115-111">O `Main` deve ser [estático](../../language-reference/keywords/static.md) e não precisa ser [público](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="f5115-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="f5115-112">(No exemplo anterior, ele recebe o acesso padrão de [Private](../../language-reference/keywords/private.md).) A classe ou struct delimitador não precisa ser estático.</span><span class="sxs-lookup"><span data-stu-id="f5115-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="f5115-113">O `Main` pode ter um tipo de retorno `void`, `int` ou, a partir do C# 7.1, `Task` ou `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="f5115-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="f5115-114">Se e somente se `Main` o retornar `Task` um `Task<int>`ou, a Declaração `Main` de poderá incluir [`async`](../../language-reference/keywords/async.md) o modificador.</span><span class="sxs-lookup"><span data-stu-id="f5115-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="f5115-115">Observe que isso exclui especificamente um método `async void Main`.</span><span class="sxs-lookup"><span data-stu-id="f5115-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="f5115-116">O método `Main` pode ser declarado com ou sem um parâmetro `string[]` que contém os argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f5115-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="f5115-117">Ao usar o Visual Studio para criar aplicativos do Windows, você pode adicionar o parâmetro manualmente ou, <xref:System.Environment.GetCommandLineArgs> caso contrário, usar o método para obter os [argumentos de linha de comando](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="f5115-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="f5115-118">Os parâmetros são lidos como argumentos de linha de comando indexados por zero.</span><span class="sxs-lookup"><span data-stu-id="f5115-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="f5115-119">Ao contrário de C e C++, o nome do programa não é tratado como o primeiro argumento de linha de comando `args` na matriz, mas é o primeiro elemento do <xref:System.Environment.GetCommandLineArgs> método.</span><span class="sxs-lookup"><span data-stu-id="f5115-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="f5115-120">Veja a seguir uma lista de assinaturas `Main` válidas:</span><span class="sxs-lookup"><span data-stu-id="f5115-120">The following is a list of valid `Main` signatures:</span></span>

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

<span data-ttu-id="f5115-121">Todos os exemplos anteriores usam o modificador de acessador público.</span><span class="sxs-lookup"><span data-stu-id="f5115-121">The preceding examples all use the public accessor modifier.</span></span> <span data-ttu-id="f5115-122">Isso é típico, mas não é necessário.</span><span class="sxs-lookup"><span data-stu-id="f5115-122">That is typical, but not required.</span></span>

<span data-ttu-id="f5115-123">A adição dos tipos de retorno `async`, `Task` e `Task<int>` simplifica o código do programa quando os aplicativos do console precisam iniciar e realizar operações assíncronas `await` no `Main`.</span><span class="sxs-lookup"><span data-stu-id="f5115-123">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f5115-124">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f5115-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f5115-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5115-125">See also</span></span>

- [<span data-ttu-id="f5115-126">Compilando pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="f5115-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="f5115-127">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="f5115-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f5115-128">Métodos</span><span class="sxs-lookup"><span data-stu-id="f5115-128">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="f5115-129">Dentro de um programa C#</span><span class="sxs-lookup"><span data-stu-id="f5115-129">Inside a C# Program</span></span>](../inside-a-program/index.md)
