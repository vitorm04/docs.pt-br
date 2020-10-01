---
title: Valores de retorno de Main() – Guia de Programação em C#
description: Saiba mais sobre os valores de retorno Main (). Consulte exemplos de código, código gerado pelo compilador e exibir recursos adicionais disponíveis.
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: c7521f6aef79825a8cc20d5455588a2d684b9ccb
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609597"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="b2cc7-104">Valores retornados de Main() (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b2cc7-104">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="b2cc7-105">O método `Main` pode retornar `void`:</span><span class="sxs-lookup"><span data-stu-id="b2cc7-105">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="b2cc7-106">Ele também pode retornar um `int`:</span><span class="sxs-lookup"><span data-stu-id="b2cc7-106">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="b2cc7-107">Se o valor retornado de `Main` não for usado, o retorno de `void` permite um código um pouco mais simples.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-107">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="b2cc7-108">No entanto, o retorno de um inteiro habilita o programa a comunicar informações de status para outros programas ou scripts, que invocam o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-108">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="b2cc7-109">O valor retornado de `Main` é tratado como o código de saída para o processo.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-109">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="b2cc7-110">Se `void` for retornado de `Main` , o código de saída será implicitamente `0` .</span><span class="sxs-lookup"><span data-stu-id="b2cc7-110">If `void` is returned from `Main`, the exit code will be implicitly `0`.</span></span> <span data-ttu-id="b2cc7-111">O exemplo a seguir mostra como o valor retornado de `Main` pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-111">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="b2cc7-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2cc7-112">Example</span></span>

<span data-ttu-id="b2cc7-113">Este exemplo usa as ferramentas de linha de comando do [.NET Core](../../../core/introduction.md) .</span><span class="sxs-lookup"><span data-stu-id="b2cc7-113">This example uses [.NET Core](../../../core/introduction.md) command-line tools.</span></span> <span data-ttu-id="b2cc7-114">Se você não estiver familiarizado com as ferramentas de linha de comando do .NET Core, poderá aprender sobre elas neste [artigo de introdução](../../../core/tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="b2cc7-114">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="b2cc7-115">Modifique o método `Main` em *program.cs* da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b2cc7-115">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="b2cc7-116">Quando um programa é executado no Windows, qualquer valor retornado da função `Main` é armazenado em uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-116">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="b2cc7-117">Essa variável de ambiente pode ser recuperada usando `ERRORLEVEL` um arquivo em lotes ou `$LastExitCode` do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-117">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from PowerShell.</span></span>

<span data-ttu-id="b2cc7-118">Você pode criar o aplicativo usando o comando [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="b2cc7-118">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="b2cc7-119">Em seguida, crie um script do PowerShell para executar o aplicativo e exibir o resultado.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-119">Next, create a PowerShell script to run the application and display the result.</span></span> <span data-ttu-id="b2cc7-120">Cole o código a seguir em um arquivo de texto e salve-o como `test.ps1` na pasta que contém o projeto.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-120">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="b2cc7-121">Execute o script do PowerShell digitando `test.ps1` no prompt do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-121">Run the PowerShell script by typing `test.ps1` at the PowerShell prompt.</span></span>

<span data-ttu-id="b2cc7-122">Como o código retorna zero, o arquivo em lotes relatará êxito.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-122">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="b2cc7-123">No entanto, se você alterar MainReturnValTest.cs para retornar um valor diferente de zero e, em seguida, recompilar o programa, a execução subsequente do script do PowerShell relatará falha.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-123">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the PowerShell script will report failure.</span></span>

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="b2cc7-124">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="b2cc7-124">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="b2cc7-125">Valores retornados de Async Main</span><span class="sxs-lookup"><span data-stu-id="b2cc7-125">Async Main return values</span></span>

<span data-ttu-id="b2cc7-126">Os valores retornados de Async Main movem o código clichê necessário para chamar métodos assíncronos em `Main` para o código gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-126">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="b2cc7-127">Anteriormente, você precisaria gravar esse constructo para chamar código assíncrono e assegurar que o programa fosse executado até que a operação assíncrona fosse concluída:</span><span class="sxs-lookup"><span data-stu-id="b2cc7-127">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="b2cc7-128">Agora, isso pode ser substituído por:</span><span class="sxs-lookup"><span data-stu-id="b2cc7-128">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="b2cc7-129">A vantagem da nova sintaxe é que o compilador sempre gera o código correto.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-129">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="b2cc7-130">Código gerado pelo compilador</span><span class="sxs-lookup"><span data-stu-id="b2cc7-130">Compiler-generated code</span></span>

<span data-ttu-id="b2cc7-131">Quando o ponto de entrada do aplicativo retorna um `Task` ou `Task<int>`, o compilador gera um novo ponto de entrada que chama o método de ponto de entrada declarado no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-131">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="b2cc7-132">Supondo que esse ponto de entrada é chamado `$GeneratedMain`, o compilador gera o código a seguir para esses pontos de entrada:</span><span class="sxs-lookup"><span data-stu-id="b2cc7-132">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="b2cc7-133">`static Task Main()` resulta no compilador emitindo o equivalente a `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="b2cc7-133">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="b2cc7-134">`static Task Main(string[])` resulta no compilador emitindo o equivalente a `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="b2cc7-134">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="b2cc7-135">`static Task<int> Main()` resulta no compilador emitindo o equivalente a `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="b2cc7-135">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="b2cc7-136">`static Task<int> Main(string[])` resulta no compilador emitindo o equivalente a `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="b2cc7-136">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="b2cc7-137">Se os exemplos usassem o modificador `async` no método `Main`, o compilador geraria o mesmo código.</span><span class="sxs-lookup"><span data-stu-id="b2cc7-137">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2cc7-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="b2cc7-138">See also</span></span>

- [<span data-ttu-id="b2cc7-139">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b2cc7-139">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b2cc7-140">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="b2cc7-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b2cc7-141">Argumentos Main () e de linha de comando</span><span class="sxs-lookup"><span data-stu-id="b2cc7-141">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="b2cc7-142">Como exibir argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="b2cc7-142">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
