---
title: Estrutura de um programa em C# - um tour pela linguagem C#
description: Saiba mais sobre os blocos de construção básicos de um programa em C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156825"
---
# <a name="program-structure"></a><span data-ttu-id="788a1-103">Estrutura do programa</span><span class="sxs-lookup"><span data-stu-id="788a1-103">Program Structure</span></span>

<span data-ttu-id="788a1-104">Os principais conceitos organizacionais em C# são ***programas***, ***namespaces***, ***tipos***, ***membros*** e ***assemblies***.</span><span class="sxs-lookup"><span data-stu-id="788a1-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="788a1-105">Os programas C# consistem em um ou mais arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="788a1-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="788a1-106">Os programas declaram tipos que contêm membros e podem ser organizados em namespaces.</span><span class="sxs-lookup"><span data-stu-id="788a1-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="788a1-107">Classes e interfaces são exemplos de tipos.</span><span class="sxs-lookup"><span data-stu-id="788a1-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="788a1-108">Campos, métodos, propriedades e eventos são exemplos de membros.</span><span class="sxs-lookup"><span data-stu-id="788a1-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="788a1-109">Quando os programas C# são compilados, eles são fisicamente embalados em assembléias.</span><span class="sxs-lookup"><span data-stu-id="788a1-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="788a1-110">Os assemblies normalmente têm a extensão de arquivo `.exe` ou `.dll`, dependendo se eles implementam ***aplicativos*** ou ***bibliotecas***, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="788a1-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="788a1-111">Você pode criar um projeto de `dotnet new` biblioteca chamado *acme* usando o comando:</span><span class="sxs-lookup"><span data-stu-id="788a1-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="788a1-112">Nesse projeto, declare uma `Stack` classe nomeada `Acme.Collections`em um namespace chamado :</span><span class="sxs-lookup"><span data-stu-id="788a1-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="788a1-113">O nome totalmente qualificado dessa classe é `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="788a1-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="788a1-114">A classe contém vários membros: um campo chamado `top`, dois métodos chamados `Push` e `Pop` e uma classe aninhada chamada `Entry`.</span><span class="sxs-lookup"><span data-stu-id="788a1-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="788a1-115">A classe `Entry` ainda contém três membros: um campo chamado `next`, um campo chamado `data`e um construtor.</span><span class="sxs-lookup"><span data-stu-id="788a1-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="788a1-116">O comando:</span><span class="sxs-lookup"><span data-stu-id="788a1-116">The command:</span></span>

```console
dotnet build
```

<span data-ttu-id="788a1-117">compila o exemplo como uma biblioteca (o código sem um ponto de entrada `Main`) e produz um assembly denominado `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="788a1-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="788a1-118">Os assemblies contêm código executável na forma de instruções de IL (Linguagem Intermediária) e informações simbólicas na forma de metadados.</span><span class="sxs-lookup"><span data-stu-id="788a1-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="788a1-119">Antes de ser executado, o compilador Just-In-Time (JIT) do .NET Common Language Runtime converte o código IL em um conjunto para um código específico do processador.</span><span class="sxs-lookup"><span data-stu-id="788a1-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="788a1-120">Como um conjunto é uma unidade de funcionalidade auto-descrevendo que contém código e `#include` metadados, não há necessidade de diretivas e arquivos de cabeçalho em C#.</span><span class="sxs-lookup"><span data-stu-id="788a1-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="788a1-121">Os tipos públicos e os membros contidos em um assembly específico são disponibilizados em um programa C# simplesmente fazendo referência a esse assembly ao compilar o programa.</span><span class="sxs-lookup"><span data-stu-id="788a1-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="788a1-122">Por exemplo, esse programa usa a classe `Acme.Collections.Stack` do assembly `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="788a1-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="788a1-123">O arquivo *csproj* para o projeto do programa anterior deve incluir um nó de referência para `acme.dll` o compilador C# para resolver referências às classes na montagem:</span><span class="sxs-lookup"><span data-stu-id="788a1-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="788a1-124">Após essa `dotnet build` adição, cria `example.exe`um conjunto executável chamado , que, quando executado, produz a saída:</span><span class="sxs-lookup"><span data-stu-id="788a1-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="788a1-125">O C# permite que o texto de origem de um programa seja armazenado em vários arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="788a1-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="788a1-126">Quando um programa em C# com vários arquivo é compilado, todos os arquivos de origem são processados juntos e os arquivos de origem podem referenciar livremente uns aos outros. Conceitualmente, é como se todos os arquivos de origem fossem concatenados em um arquivo grande antes de serem processados.</span><span class="sxs-lookup"><span data-stu-id="788a1-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="788a1-127">As declarações avançadas nunca são necessárias em C# porque, com poucas exceções, a ordem de declaração é insignificante.</span><span class="sxs-lookup"><span data-stu-id="788a1-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="788a1-128">O C# não limita um arquivo de origem para declarar somente um tipo público nem requer o nome do arquivo de origem para corresponder a um tipo declarado no arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="788a1-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="788a1-129">[Próximo](index.md)
>[anterior](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="788a1-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
