---
title: Estrutura de um programa em C# - um tour pela linguagem C#
description: "Saiba mais sobre os blocos de construção básicos de um programa em C#"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 8d8f443f8458cd392c75e9787e612ca1cc3518c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="program-structure"></a><span data-ttu-id="eb8f0-104">Estrutura do programa</span><span class="sxs-lookup"><span data-stu-id="eb8f0-104">Program Structure</span></span>

<span data-ttu-id="eb8f0-105">Os principais conceitos organizacionais em C# são ***programas***, ***namespaces***, ***tipos***, ***membros*** e ***assemblies***.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-105">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="eb8f0-106">Os programas C# consistem em um ou mais arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-106">C# programs consist of one or more source files.</span></span> <span data-ttu-id="eb8f0-107">Os programas declaram tipos que contêm membros e podem ser organizados em namespaces.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-107">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="eb8f0-108">Classes e interfaces são exemplos de tipos.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-108">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="eb8f0-109">Campos, métodos, propriedades e eventos são exemplos de membros.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-109">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="eb8f0-110">Quando os programas em C# são compilados, eles são empacotados fisicamente em assemblies.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-110">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="eb8f0-111">Os assemblies normalmente têm a extensão de arquivo `.exe` ou `.dll`, dependendo se eles implementam ***aplicativos*** ou ***bibliotecas***, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-111">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="eb8f0-112">O exemplo declara uma classe chamada `Stack` em um namespace chamado `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="eb8f0-112">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="eb8f0-113">O nome totalmente qualificado dessa classe é `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="eb8f0-114">A classe contém vários membros: um campo chamado `top`, dois métodos chamados `Push` e `Pop` e uma classe aninhada chamada `Entry`.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="eb8f0-115">A classe `Entry` ainda contém três membros: um campo chamado `next`, um campo chamado `data`e um construtor.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="eb8f0-116">Supondo que o código-fonte do exemplo seja armazenado no arquivo `acme.cs`, a linha de comando</span><span class="sxs-lookup"><span data-stu-id="eb8f0-116">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="eb8f0-117">compila o exemplo como uma biblioteca (o código sem um ponto de entrada `Main`) e produz um assembly denominado `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb8f0-118">Os exemplos acima usam `csc` como o compilador C# da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-118">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="eb8f0-119">Esse compilador é um executável do Windows.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-119">This compiler is a windows executable.</span></span> <span data-ttu-id="eb8f0-120">Para usar C# em outras plataformas, você deve usar as ferramentas para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-120">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="eb8f0-121">O ecossistema do .NET Core usa o CLI `dotnet` para gerenciar as compilações de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-121">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="eb8f0-122">Isso inclui gerenciamento de dependências e invocação do compilador C#.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-122">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="eb8f0-123">Consulte [este tutorial](../../core/tutorials/using-with-xplat-cli.md) para obter uma descrição completa dessas ferramentas nas plataformas com suporte do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-123">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="eb8f0-124">Os assemblies contêm código executável na forma de instruções de IL (Linguagem Intermediária) e informações simbólicas na forma de metadados.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-124">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="eb8f0-125">Antes de ser executado, o código de IL em um assembly é automaticamente convertido em código específico do processador pelo compilador JIT (Just-In-Time) do .NET Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-125">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="eb8f0-126">Como um assembly é uma unidade autodescritiva da funcionalidade que contém o código e os metadados, não é necessário de diretivas `#include` e arquivos de cabeçalho no C#.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-126">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="eb8f0-127">Os tipos públicos e os membros contidos em um assembly específico são disponibilizados em um programa C# simplesmente fazendo referência a esse assembly ao compilar o programa.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-127">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="eb8f0-128">Por exemplo, esse programa usa a classe `Acme.Collections.Stack` do assembly `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="eb8f0-128">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="eb8f0-129">Se o programa é armazenado no arquivo `example.cs`, quando `example.cs` é compilado, o assembly acme.dll pode ser referenciado usando a opção de /r do compilador:</span><span class="sxs-lookup"><span data-stu-id="eb8f0-129">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="eb8f0-130">Isso cria um assembly executável denominado `example.exe`, que, quando executado, produz a saída:</span><span class="sxs-lookup"><span data-stu-id="eb8f0-130">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="eb8f0-131">O C# permite que o texto de origem de um programa seja armazenado em vários arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-131">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="eb8f0-132">Quando um programa em C# com vários arquivo é compilado, todos os arquivos de origem são processados juntos e os arquivos de origem podem referenciar livremente uns aos outros. Conceitualmente, é como se todos os arquivos de origem fossem concatenados em um arquivo grande antes de serem processados.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-132">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="eb8f0-133">Declarações de encaminhamento nunca são necessárias em C#, porque, com poucas exceções, a ordem de declaração é insignificante.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-133">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="eb8f0-134">O C# não limita um arquivo de origem para declarar somente um tipo público nem requer o nome do arquivo de origem para corresponder a um tipo declarado no arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="eb8f0-134">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="eb8f0-135">[Anterior](index.md)
[Próximo](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="eb8f0-135">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
