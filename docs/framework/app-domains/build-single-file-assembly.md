---
title: Como compilar um .NET Framework assembly de arquivo único
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: af1bfb89b01a316a858cbb45bf19a26a16d90016
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119944"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="c52c1-102">Como compilar um .NET Framework assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="c52c1-102">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="c52c1-103">Um assembly de arquivo único, que é o tipo mais simples de assembly, contém informações sobre o tipo e a implementação, bem como o [manifesto do assembly](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="c52c1-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="c52c1-104">Você pode usar compiladores de linha de comando ou o Visual Studio para criar um assembly de arquivo único que tenha como destino o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c52c1-104">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="c52c1-105">Por padrão, o compilador cria um arquivo de assembly com uma extensão *. exe* .</span><span class="sxs-lookup"><span data-stu-id="c52c1-105">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="c52c1-106">O Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="c52c1-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="c52c1-107">Se quiser criar assemblies de vários arquivos, você deverá usar os compiladores de linha de comando ou o Visual C++.</span><span class="sxs-lookup"><span data-stu-id="c52c1-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="c52c1-108">Os procedimentos a seguir mostram como criar assemblies de arquivo único usando compiladores de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c52c1-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="c52c1-109">Criar um assembly com uma extensão. exe</span><span class="sxs-lookup"><span data-stu-id="c52c1-109">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="c52c1-110">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c52c1-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="c52c1-111">\<*comando do compilador*> \<*nome do módulo*></span><span class="sxs-lookup"><span data-stu-id="c52c1-111">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="c52c1-112">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="c52c1-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="c52c1-113">O exemplo a seguir cria um assembly chamado *myCode. exe* a partir de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="c52c1-113">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="c52c1-114">Criar um assembly com uma extensão. exe e especificar o nome do arquivo de saída</span><span class="sxs-lookup"><span data-stu-id="c52c1-114">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="c52c1-115">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c52c1-115">At the command prompt, type the following command:</span></span>

<span data-ttu-id="c52c1-116">\<*comando do compilador*>  **/out:** \<*nome de arquivo*> \<*nome do módulo*></span><span class="sxs-lookup"><span data-stu-id="c52c1-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="c52c1-117">Neste comando, o *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código, *nome de arquivo* é o nome de arquivo de saída e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="c52c1-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="c52c1-118">O exemplo a seguir cria um assembly chamado *myAssembly. exe* a partir de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="c52c1-118">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="c52c1-119">Criar assemblies de biblioteca</span><span class="sxs-lookup"><span data-stu-id="c52c1-119">Create library assemblies</span></span>
 <span data-ttu-id="c52c1-120">Um assembly de biblioteca é semelhante a uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="c52c1-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="c52c1-121">Ele contém tipos que serão referenciados por outros assemblies, mas ele não tem nenhum ponto de entrada para iniciar a execução.</span><span class="sxs-lookup"><span data-stu-id="c52c1-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="c52c1-122">Para criar um assembly de biblioteca, no prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c52c1-122">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="c52c1-123">\<*compiler command*>  **-t:library** \<*module name*></span><span class="sxs-lookup"><span data-stu-id="c52c1-123">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="c52c1-124">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="c52c1-124">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="c52c1-125">Você também pode usar outras opções do compilador, como a opção **-out:** .</span><span class="sxs-lookup"><span data-stu-id="c52c1-125">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="c52c1-126">O exemplo a seguir cria um assembly de biblioteca chamado *myCodeAssembly. dll* a partir de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="c52c1-126">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="c52c1-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c52c1-127">See also</span></span>

- [<span data-ttu-id="c52c1-128">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="c52c1-128">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="c52c1-129">Assemblies de multiarquivo</span><span class="sxs-lookup"><span data-stu-id="c52c1-129">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="c52c1-130">Como compilar um assembly de multiarquivos</span><span class="sxs-lookup"><span data-stu-id="c52c1-130">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="c52c1-131">Programa com assemblies</span><span class="sxs-lookup"><span data-stu-id="c52c1-131">Program with assemblies</span></span>](../../standard/assembly/program.md)
