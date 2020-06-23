---
title: Como compilar um .NET Framework assembly de arquivo único
description: Explore como criar um assembly de arquivo único no .NET. Um assembly de arquivo único pode ser uma biblioteca (. dll) que tem como destino o .NET ou pode ser um arquivo executável (. exe).
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
ms.openlocfilehash: 482a973631e899b8d4bfc4640eef1ea26173605e
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104920"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="e32b5-104">Como compilar um .NET Framework assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="e32b5-104">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="e32b5-105">Um assembly de arquivo único, que é o tipo mais simples de assembly, contém informações sobre o tipo e a implementação, bem como o [manifesto do assembly](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="e32b5-105">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="e32b5-106">Você pode usar compiladores de linha de comando ou o Visual Studio para criar um assembly de arquivo único que tenha como destino o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e32b5-106">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="e32b5-107">Por padrão, o compilador cria um arquivo de assembly com uma extensão *. exe* .</span><span class="sxs-lookup"><span data-stu-id="e32b5-107">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="e32b5-108">O Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="e32b5-108">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="e32b5-109">Se quiser criar assemblies de vários arquivos, você deverá usar os compiladores de linha de comando ou o Visual C++.</span><span class="sxs-lookup"><span data-stu-id="e32b5-109">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="e32b5-110">Os procedimentos a seguir mostram como criar assemblies de arquivo único usando compiladores de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e32b5-110">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="e32b5-111">Criar um assembly com uma extensão. exe</span><span class="sxs-lookup"><span data-stu-id="e32b5-111">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="e32b5-112">No prompt de comando, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="e32b5-112">At the command prompt, type the following command:</span></span>

<span data-ttu-id="e32b5-113">\<*compiler command*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="e32b5-113">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="e32b5-114">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="e32b5-114">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="e32b5-115">O exemplo a seguir cria um assembly chamado *myCode.exe* de um módulo de código chamado `myCode` .</span><span class="sxs-lookup"><span data-stu-id="e32b5-115">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="e32b5-116">Criar um assembly com uma extensão. exe e especificar o nome do arquivo de saída</span><span class="sxs-lookup"><span data-stu-id="e32b5-116">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="e32b5-117">No prompt de comando, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="e32b5-117">At the command prompt, type the following command:</span></span>

<span data-ttu-id="e32b5-118">\<*compiler command*>**/out:** \<*file name*>\<*module name*></span><span class="sxs-lookup"><span data-stu-id="e32b5-118">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="e32b5-119">Neste comando, o *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código, *nome de arquivo* é o nome de arquivo de saída e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="e32b5-119">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="e32b5-120">O exemplo a seguir cria um assembly chamado *myAssembly.exe* de um módulo de código chamado `myCode` .</span><span class="sxs-lookup"><span data-stu-id="e32b5-120">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="e32b5-121">Criar assemblies de biblioteca</span><span class="sxs-lookup"><span data-stu-id="e32b5-121">Create library assemblies</span></span>
 <span data-ttu-id="e32b5-122">Um assembly de biblioteca é semelhante a uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="e32b5-122">A library assembly is similar to a class library.</span></span> <span data-ttu-id="e32b5-123">Ele contém tipos que serão referenciados por outros assemblies, mas ele não tem nenhum ponto de entrada para iniciar a execução.</span><span class="sxs-lookup"><span data-stu-id="e32b5-123">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="e32b5-124">Para criar um assembly de biblioteca, no prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e32b5-124">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="e32b5-125">\<*compiler command*>**-t:library**\<*module name*></span><span class="sxs-lookup"><span data-stu-id="e32b5-125">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="e32b5-126">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="e32b5-126">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="e32b5-127">Você também pode usar outras opções de compilador, como a opção **-out:** .</span><span class="sxs-lookup"><span data-stu-id="e32b5-127">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="e32b5-128">O exemplo a seguir cria um assembly de biblioteca chamado *myCodeAssembly.dll* de um módulo de código chamado `myCode` .</span><span class="sxs-lookup"><span data-stu-id="e32b5-128">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="e32b5-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="e32b5-129">See also</span></span>

- [<span data-ttu-id="e32b5-130">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="e32b5-130">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="e32b5-131">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="e32b5-131">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="e32b5-132">Como: criar um assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="e32b5-132">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="e32b5-133">Programar com assemblies</span><span class="sxs-lookup"><span data-stu-id="e32b5-133">Program with assemblies</span></span>](../../standard/assembly/index.md)
