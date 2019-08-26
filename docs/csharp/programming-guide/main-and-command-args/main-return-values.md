---
title: Valores de retorno de Main() – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 1be04f98a4dec1317c485c7e482568cfe48ea9bf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588886"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="99414-102">Valores retornados de Main() (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="99414-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="99414-103">O método `Main` pode retornar `void`:</span><span class="sxs-lookup"><span data-stu-id="99414-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="99414-104">Ele também pode retornar um `int`:</span><span class="sxs-lookup"><span data-stu-id="99414-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="99414-105">Se o valor retornado de `Main` não for usado, o retorno de `void` permite um código um pouco mais simples.</span><span class="sxs-lookup"><span data-stu-id="99414-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="99414-106">No entanto, o retorno de um inteiro habilita o programa a comunicar informações de status para outros programas ou scripts, que invocam o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="99414-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="99414-107">O valor retornado de `Main` é tratado como o código de saída para o processo.</span><span class="sxs-lookup"><span data-stu-id="99414-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="99414-108">Se `void` for retornado de `Main`, o código de saída será implicitamente `0`.</span><span class="sxs-lookup"><span data-stu-id="99414-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="99414-109">O exemplo a seguir mostra como o valor retornado de `Main` pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="99414-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="99414-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99414-110">Example</span></span>

<span data-ttu-id="99414-111">Este exemplo usa ferramentas de linha de comando do [.NET Core](../../../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="99414-111">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="99414-112">Se você não estiver familiarizado com as ferramentas de linha de comando do .NET Core, poderá aprender sobre elas neste [Tópico de introdução](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="99414-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="99414-113">Modifique o método `Main` em *program.cs* da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="99414-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="99414-114">Quando um programa é executado no Windows, qualquer valor retornado da função `Main` é armazenado em uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="99414-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="99414-115">Essa variável de ambiente pode ser recuperada usando `ERRORLEVEL` de um arquivo em lotes ou `$LastExitCode` do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99414-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="99414-116">Você pode criar o aplicativo usando o comando `dotnet build` da [CLI do dotnet](../../../core/tools/dotnet.md).</span><span class="sxs-lookup"><span data-stu-id="99414-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="99414-117">Em seguida, crie um script do Powershell para executar o aplicativo e exibir o resultado.</span><span class="sxs-lookup"><span data-stu-id="99414-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="99414-118">Cole o código a seguir em um arquivo de texto e salve-o como `test.ps1` na pasta que contém o projeto.</span><span class="sxs-lookup"><span data-stu-id="99414-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="99414-119">Execute o script do PowerShell digitando `test.ps1` no prompt do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99414-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="99414-120">Como o código retorna zero, o arquivo em lotes relatará êxito.</span><span class="sxs-lookup"><span data-stu-id="99414-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="99414-121">No entanto, se você alterar o MainReturnValTest.cs para retornar um valor diferente de zero e recompilar o programa, a execução subsequente do script do PowerShell reportará falha.</span><span class="sxs-lookup"><span data-stu-id="99414-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="99414-122">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="99414-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="99414-123">Valores retornados de Async Main</span><span class="sxs-lookup"><span data-stu-id="99414-123">Async Main return values</span></span>

<span data-ttu-id="99414-124">Os valores retornados de Async Main movem o código clichê necessário para chamar métodos assíncronos em `Main` para o código gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="99414-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="99414-125">Anteriormente, você precisaria gravar esse constructo para chamar código assíncrono e assegurar que o programa fosse executado até que a operação assíncrona fosse concluída:</span><span class="sxs-lookup"><span data-stu-id="99414-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="99414-126">Agora, isso pode ser substituído por:</span><span class="sxs-lookup"><span data-stu-id="99414-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="99414-127">A vantagem da nova sintaxe é que o compilador sempre gera o código correto.</span><span class="sxs-lookup"><span data-stu-id="99414-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="99414-128">Código gerado pelo compilador</span><span class="sxs-lookup"><span data-stu-id="99414-128">Compiler generated code</span></span>

<span data-ttu-id="99414-129">Quando o ponto de entrada do aplicativo retorna um `Task` ou `Task<int>`, o compilador gera um novo ponto de entrada que chama o método de ponto de entrada declarado no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99414-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="99414-130">Supondo que esse ponto de entrada é chamado `$GeneratedMain`, o compilador gera o código a seguir para esses pontos de entrada:</span><span class="sxs-lookup"><span data-stu-id="99414-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="99414-131">`static Task Main()` resulta no compilador emitindo o equivalente a `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="99414-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="99414-132">`static Task Main(string[])` resulta no compilador emitindo o equivalente a `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="99414-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="99414-133">`static Task<int> Main()` resulta no compilador emitindo o equivalente a `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="99414-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="99414-134">`static Task<int> Main(string[])` resulta no compilador emitindo o equivalente a `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="99414-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="99414-135">Se os exemplos usassem o modificador `async` no método `Main`, o compilador geraria o mesmo código.</span><span class="sxs-lookup"><span data-stu-id="99414-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="99414-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99414-136">See also</span></span>

- [<span data-ttu-id="99414-137">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="99414-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="99414-138">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="99414-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="99414-139">Main() e argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="99414-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="99414-140">Como: exibir argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="99414-140">How to: Display Command Line Arguments</span></span>](./how-to-display-command-line-arguments.md)
