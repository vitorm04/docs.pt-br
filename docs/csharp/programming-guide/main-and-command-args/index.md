---
title: Main() e argumentos de linha de comando – Guia de Programação em C#
ms.custom: seodec18
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
ms.openlocfilehash: a5707e8cfff11dd9d27fffc9deb41662fb2c4460
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281760"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="ede9c-102">Main() e argumentos de linha de comando (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ede9c-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="ede9c-103">O método `Main` é o ponto de entrada de um aplicativo C#.</span><span class="sxs-lookup"><span data-stu-id="ede9c-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="ede9c-104">(As bibliotecas e os serviços não exigem um método `Main` como um ponto de entrada.) Quando o aplicativo é iniciado, o método `Main` é o primeiro método que é invocado.</span><span class="sxs-lookup"><span data-stu-id="ede9c-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="ede9c-105">Pode haver apenas um ponto de entrada em um programa C#.</span><span class="sxs-lookup"><span data-stu-id="ede9c-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="ede9c-106">Se tiver mais de uma classe que tenha um `Main` método, você deverá compilar seu programa com a opção do compilador **/main** para especificar qual método `Main` será usado como ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="ede9c-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="ede9c-107">Para obter mais informações, consulte [-MainC# (opções do compilador)](../../language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ede9c-107">For more information, see [-main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a><span data-ttu-id="ede9c-108">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ede9c-108">Overview</span></span>

- <span data-ttu-id="ede9c-109">O método `Main` é o ponto de entrada de um programa executável; é onde o controle do programa começa e termina.</span><span class="sxs-lookup"><span data-stu-id="ede9c-109">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="ede9c-110">`Main` é declarado dentro de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="ede9c-110">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="ede9c-111">O `Main` deve ser [estático](../../language-reference/keywords/static.md) e não precisa ser [público](../../language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="ede9c-111">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="ede9c-112">(No exemplo anterior, ele recebe o acesso padrão de [Private](../../language-reference/keywords/private.md).) A classe ou struct delimitador não precisa ser estático.</span><span class="sxs-lookup"><span data-stu-id="ede9c-112">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="ede9c-113">O `Main` pode ter um tipo de retorno `void`, `int` ou, a partir do C# 7.1, `Task` ou `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="ede9c-113">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="ede9c-114">Se e somente se `Main` retornar um `Task` ou `Task<int>`, a declaração de `Main` pode incluir o modificador [`async`](../../language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="ede9c-114">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ede9c-115">Observe que isso exclui especificamente um método `async void Main`.</span><span class="sxs-lookup"><span data-stu-id="ede9c-115">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="ede9c-116">O método `Main` pode ser declarado com ou sem um parâmetro `string[]` que contém os argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ede9c-116">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="ede9c-117">Ao usar o Visual Studio para criar aplicativos do Windows, você pode adicionar o parâmetro manualmente ou, caso contrário, usar o método <xref:System.Environment.GetCommandLineArgs> para obter os [argumentos de linha de comando](command-line-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="ede9c-117">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="ede9c-118">Os parâmetros são lidos como argumentos de linha de comando indexados por zero.</span><span class="sxs-lookup"><span data-stu-id="ede9c-118">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="ede9c-119">Ao contrário de C++C e, o nome do programa não é tratado como o primeiro argumento de linha de comando na matriz de `args`, mas é o primeiro elemento do método <xref:System.Environment.GetCommandLineArgs>.</span><span class="sxs-lookup"><span data-stu-id="ede9c-119">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="ede9c-120">A seguir está uma lista de assinaturas de `Main` válidas:</span><span class="sxs-lookup"><span data-stu-id="ede9c-120">The following is a list of valid `Main` signatures:</span></span>

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

<span data-ttu-id="ede9c-121">A adição dos tipos de retorno `async`, `Task` e `Task<int>` simplifica o código do programa quando os aplicativos do console precisam iniciar e realizar operações assíncronas `await` no `Main`.</span><span class="sxs-lookup"><span data-stu-id="ede9c-121">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ede9c-122">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ede9c-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ede9c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ede9c-123">See also</span></span>

- [<span data-ttu-id="ede9c-124">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="ede9c-124">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="ede9c-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ede9c-125">C# Programming Guide</span></span>](../index.md)
- <span data-ttu-id="ede9c-126">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ede9c-126">[Methods](../classes-and-structs/methods.md)</span></span>
- [<span data-ttu-id="ede9c-127">Por dentro de um programa em C#</span><span class="sxs-lookup"><span data-stu-id="ede9c-127">Inside a C# Program</span></span>](../inside-a-program/index.md)
