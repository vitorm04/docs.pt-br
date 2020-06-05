---
title: Escrever um programa paralelo simples usando Parallel.ForEach
description: Neste artigo, saiba como habilitar o paralelismo de dados no .NET. Escreva um loop Parallel. ForEach em qualquer fonte de dados IEnumerable ou IEnumerable <T> .
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 59c8710a8e3fc878b2ceded8595f7f3319d4c953
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447193"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="b86c8-104">Como: gravar um loop Parallel. ForEach simples</span><span class="sxs-lookup"><span data-stu-id="b86c8-104">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="b86c8-105">Este exemplo mostra como usar um loop <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> para permitir o paralelismo de dados em relação a qualquer fonte de dados <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b86c8-105">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="b86c8-106">Esta documentação usa expressões lambda para definir representantes na PLINQ.</span><span class="sxs-lookup"><span data-stu-id="b86c8-106">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="b86c8-107">Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, confira [Expressões Lambda em PLINQ e TPL](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="b86c8-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="b86c8-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b86c8-108">Example</span></span>

<span data-ttu-id="b86c8-109">Este exemplo considera que você tenha vários arquivos .jpg em uma pasta *C:\Users\Public\Pictures\Sample Pictures* e crie uma subpasta chamada *Modified*.</span><span class="sxs-lookup"><span data-stu-id="b86c8-109">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="b86c8-110">Quando você executa o exemplo, ele gira cada imagem .jpg em *Amostras de Imagens* e salva-a em *Modified*.</span><span class="sxs-lookup"><span data-stu-id="b86c8-110">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="b86c8-111">Você pode modificar os dois caminhos, conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="b86c8-111">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="b86c8-112">Um loop <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> funciona como um loop <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b86c8-112">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="b86c8-113">O loop particiona a coleção de origem e agenda o trabalho em vários threads com base no ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="b86c8-113">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="b86c8-114">Quanto mais processadores houver no sistema, mais rápido o método paralelo será executado.</span><span class="sxs-lookup"><span data-stu-id="b86c8-114">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="b86c8-115">Para algumas coleções de origem, um loop sequencial pode ser mais rápido, dependendo do tamanho da origem e do tipo de trabalho que o loop executa.</span><span class="sxs-lookup"><span data-stu-id="b86c8-115">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="b86c8-116">Para obter mais informações sobre o desempenho, consulte [possíveis armadilhas em dados e paralelismo de tarefas](potential-pitfalls-in-data-and-task-parallelism.md).</span><span class="sxs-lookup"><span data-stu-id="b86c8-116">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="b86c8-117">Para obter mais informações sobre loops paralelos, consulte [como: gravar um loop Parallel. for simples](how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="b86c8-117">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="b86c8-118">Para usar <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> com uma coleção não genérica, você pode usar o método de extensão <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> para converter a coleção em uma coleção genérica, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b86c8-118">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="b86c8-119">Você também pode usar o LINQ Paralelo (PLINQ) para efetuar a paralelização de processamento de fontes de dados <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b86c8-119">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="b86c8-120">O PLINQ permite que você use a sintaxe de consulta declarativa para expressar o comportamento do loop.</span><span class="sxs-lookup"><span data-stu-id="b86c8-120">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="b86c8-121">Para obter mais informações, consulte [PLINQ (Parallel LINQ)](introduction-to-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="b86c8-121">For more information, see [Parallel LINQ (PLINQ)](introduction-to-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="b86c8-122">Compilar e executar o código</span><span class="sxs-lookup"><span data-stu-id="b86c8-122">Compile and run the code</span></span>

<span data-ttu-id="b86c8-123">Você pode compilar o código como um aplicativo de console do .NET Framework ou do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b86c8-123">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="b86c8-124">No Visual Studio, há modelos de aplicativo de console do Visual Basic e do C# para a área de trabalho do Windows e o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b86c8-124">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="b86c8-125">Na linha de comando, você pode usar os comandos de CLI do .NET Core (por exemplo, `dotnet new console` ou `dotnet new console -lang vb` ), ou pode criar o arquivo e usar o compilador de linha de comando para um aplicativo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b86c8-125">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="b86c8-126">Para um projeto do .NET Core, você precisa referenciar o pacote **System.Drawing.Common** do NuGet.</span><span class="sxs-lookup"><span data-stu-id="b86c8-126">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="b86c8-127">No Visual Studio, use o Gerenciador de Pacotes do NuGet para instalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="b86c8-127">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="b86c8-128">Como alternativa, você pode adicionar uma referência ao pacote no arquivo \*.csproj\* ou \*.vbproj\*:</span><span class="sxs-lookup"><span data-stu-id="b86c8-128">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="b86c8-129">Para executar um aplicativo de console do .NET Core na linha de comando, use `dotnet run` da pasta que contém o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b86c8-129">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="b86c8-130">Para executar o aplicativo de console do Visual Studio, pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="b86c8-130">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b86c8-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="b86c8-131">See also</span></span>

- [<span data-ttu-id="b86c8-132">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="b86c8-132">Data parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="b86c8-133">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="b86c8-133">Parallel programming</span></span>](index.md)
- [<span data-ttu-id="b86c8-134">LINQ paralelo (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b86c8-134">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
