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
ms.openlocfilehash: b7cb06da74a21dab6f60f0d4c3ac1748fcbe4526
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644296"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="abbd3-102">Como compilar um .NET Framework assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="abbd3-102">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="abbd3-103">Um assembly de arquivo único, que é o tipo mais simples de assembly, contém informações sobre o tipo e a implementação, bem como o [manifesto do assembly](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="abbd3-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="abbd3-104">Você pode usar compiladores de linha de comando ou o Visual Studio para criar um assembly de arquivo único que tenha como destino o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abbd3-104">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="abbd3-105">Por padrão, o compilador cria um arquivo de assembly com uma extensão *. exe* .</span><span class="sxs-lookup"><span data-stu-id="abbd3-105">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="abbd3-106">O Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="abbd3-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="abbd3-107">Se quiser criar assemblies de vários arquivos, você deverá usar os compiladores de linha de comando ou o Visual C++.</span><span class="sxs-lookup"><span data-stu-id="abbd3-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="abbd3-108">Os procedimentos a seguir mostram como criar assemblies de arquivo único usando compiladores de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="abbd3-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="abbd3-109">Criar um assembly com uma extensão. exe</span><span class="sxs-lookup"><span data-stu-id="abbd3-109">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="abbd3-110">No prompt de comando, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="abbd3-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="abbd3-111">\<*compiler command*> \<*nome do módulo* de comando do compilador></span><span class="sxs-lookup"><span data-stu-id="abbd3-111">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="abbd3-112">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="abbd3-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="abbd3-113">O exemplo a seguir cria um assembly chamado *myCode. exe* a partir de um `myCode`módulo de código chamado.</span><span class="sxs-lookup"><span data-stu-id="abbd3-113">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="abbd3-114">Criar um assembly com uma extensão. exe e especificar o nome do arquivo de saída</span><span class="sxs-lookup"><span data-stu-id="abbd3-114">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="abbd3-115">No prompt de comando, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="abbd3-115">At the command prompt, type the following command:</span></span>

<span data-ttu-id="abbd3-116">\<*comando*> do compilador **/out:**\<*nome*> \<do arquivo*nome do módulo*></span><span class="sxs-lookup"><span data-stu-id="abbd3-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="abbd3-117">Neste comando, o *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código, *nome de arquivo* é o nome de arquivo de saída e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="abbd3-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="abbd3-118">O exemplo a seguir cria um assembly chamado *myAssembly. exe* a partir de um `myCode`módulo de código chamado.</span><span class="sxs-lookup"><span data-stu-id="abbd3-118">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="abbd3-119">Criar assemblies de biblioteca</span><span class="sxs-lookup"><span data-stu-id="abbd3-119">Create library assemblies</span></span>
 <span data-ttu-id="abbd3-120">Um assembly de biblioteca é semelhante a uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="abbd3-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="abbd3-121">Ele contém tipos que serão referenciados por outros assemblies, mas ele não tem nenhum ponto de entrada para iniciar a execução.</span><span class="sxs-lookup"><span data-stu-id="abbd3-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="abbd3-122">Para criar um assembly de biblioteca, no prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="abbd3-122">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="abbd3-123">\<*comando*> do compilador **–** \< *nome do módulo* t:library></span><span class="sxs-lookup"><span data-stu-id="abbd3-123">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="abbd3-124">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="abbd3-124">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="abbd3-125">Você também pode usar outras opções de compilador, como a opção **-out:** .</span><span class="sxs-lookup"><span data-stu-id="abbd3-125">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="abbd3-126">O exemplo a seguir cria um assembly de biblioteca chamado *myCodeAssembly. dll* a partir de `myCode`um módulo de código chamado.</span><span class="sxs-lookup"><span data-stu-id="abbd3-126">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="abbd3-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="abbd3-127">See also</span></span>

- [<span data-ttu-id="abbd3-128">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="abbd3-128">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="abbd3-129">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="abbd3-129">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="abbd3-130">Como compilar um assembly de multiarquivos</span><span class="sxs-lookup"><span data-stu-id="abbd3-130">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="abbd3-131">Programar com assemblies</span><span class="sxs-lookup"><span data-stu-id="abbd3-131">Program with assemblies</span></span>](../../standard/assembly/index.md)
