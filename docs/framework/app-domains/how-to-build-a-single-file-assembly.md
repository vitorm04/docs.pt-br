---
title: 'Como: Criar um assembly de arquivo único'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a73b2d8948c9a046fd77c02f1bcc87f5738105d9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303993"
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="e21a7-102">Como: Criar um assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="e21a7-102">How to: Build a Single-File Assembly</span></span>

<span data-ttu-id="e21a7-103">Um assembly de arquivo único, que é o tipo mais simples de assembly, contém informações sobre o tipo e a implementação, bem como o [manifesto do assembly](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="e21a7-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="e21a7-104">Você pode usar compiladores de linha de comando ou o Visual Studio para criar um assembly de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="e21a7-104">You can use command-line compilers or Visual Studio to create a single-file assembly.</span></span> <span data-ttu-id="e21a7-105">Por padrão, o compilador cria um arquivo do assembly com uma extensão de .exe.</span><span class="sxs-lookup"><span data-stu-id="e21a7-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>

> [!NOTE]
> <span data-ttu-id="e21a7-106">O Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="e21a7-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="e21a7-107">Se quiser criar assemblies de vários arquivos, você deverá usar os compiladores de linha de comando ou o Visual C++.</span><span class="sxs-lookup"><span data-stu-id="e21a7-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="e21a7-108">Os procedimentos a seguir mostram como criar assemblies de arquivo único usando compiladores de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e21a7-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="e21a7-109">Para criar um assembly com uma extensão .exe</span><span class="sxs-lookup"><span data-stu-id="e21a7-109">To create an assembly with an .exe extension</span></span>

1. <span data-ttu-id="e21a7-110">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e21a7-110">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="e21a7-111">\<*comando do compilador*> \<*nome do módulo*></span><span class="sxs-lookup"><span data-stu-id="e21a7-111">\<*compiler command*> \<*module name*></span></span>

     <span data-ttu-id="e21a7-112">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="e21a7-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="e21a7-113">O exemplo a seguir cria um assembly chamado `myCode.exe` de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="e21a7-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="e21a7-114">Para criar um assembly com uma extensão .exe e especificar o nome do arquivo de saída</span><span class="sxs-lookup"><span data-stu-id="e21a7-114">To create an assembly with an .exe extension and specify the output file name</span></span>

1. <span data-ttu-id="e21a7-115">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e21a7-115">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="e21a7-116">\<*comando do compilador*> **/out:**\<*nome de arquivo*> \<*nome do módulo*></span><span class="sxs-lookup"><span data-stu-id="e21a7-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

     <span data-ttu-id="e21a7-117">Neste comando, o *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código, *nome de arquivo* é o nome de arquivo de saída e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="e21a7-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="e21a7-118">O exemplo a seguir cria um assembly chamado `myAssembly.exe` de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="e21a7-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a><span data-ttu-id="e21a7-119">Criando assemblies de biblioteca</span><span class="sxs-lookup"><span data-stu-id="e21a7-119">Creating Library Assemblies</span></span>
 <span data-ttu-id="e21a7-120">Um assembly de biblioteca é semelhante a uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="e21a7-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="e21a7-121">Ele contém tipos que serão referenciados por outros assemblies, mas ele não tem nenhum ponto de entrada para iniciar a execução.</span><span class="sxs-lookup"><span data-stu-id="e21a7-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

### <a name="to-create-a-library-assembly"></a><span data-ttu-id="e21a7-122">Para criar um assembly de biblioteca</span><span class="sxs-lookup"><span data-stu-id="e21a7-122">To create a library assembly</span></span>

1. <span data-ttu-id="e21a7-123">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e21a7-123">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="e21a7-124">\<*compiler command*> **-t:library** \<*module name*></span><span class="sxs-lookup"><span data-stu-id="e21a7-124">\<*compiler command*> **-t:library** \<*module name*></span></span>

     <span data-ttu-id="e21a7-125">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="e21a7-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="e21a7-126">Você também pode usar outras opções do compilador, como a opção **-out:**.</span><span class="sxs-lookup"><span data-stu-id="e21a7-126">You can also use other compiler options, such as the **-out:** option.</span></span>

 <span data-ttu-id="e21a7-127">O exemplo a seguir cria um assembly de biblioteca chamado `myCodeAssembly.dll` de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="e21a7-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="e21a7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e21a7-128">See also</span></span>

- [<span data-ttu-id="e21a7-129">Criando assemblies</span><span class="sxs-lookup"><span data-stu-id="e21a7-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="e21a7-130">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="e21a7-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="e21a7-131">Como: Criar um assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="e21a7-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="e21a7-132">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="e21a7-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)