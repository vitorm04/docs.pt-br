---
title: "Como compilar um assembly de vários arquivos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68a2217ed05588b2ba6070850dfd0d61a7a0fde2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="07456-102">Como compilar um assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="07456-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="07456-103">Este artigo explica como criar um assembly de vários arquivos e fornece código que ilustra cada etapa no procedimento.</span><span class="sxs-lookup"><span data-stu-id="07456-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07456-104">O IDE do Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="07456-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="07456-105">Se quiser criar assemblies de vários arquivos, você precisará usar os compiladores de linha de comando ou Visual Studio com o Visual C++.</span><span class="sxs-lookup"><span data-stu-id="07456-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="07456-106">Para criar um assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="07456-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="07456-107">Compile todos os arquivos que contêm namespaces referenciados por outros módulos no assembly nos módulos de código.</span><span class="sxs-lookup"><span data-stu-id="07456-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="07456-108">A extensão padrão para módulos de código é .netmodule.</span><span class="sxs-lookup"><span data-stu-id="07456-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="07456-109">Por exemplo, digamos que o arquivo `Stringer` tem um namespace chamado `myStringer`, que inclui uma classe chamada `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="07456-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="07456-110">A classe `Stringer` contém um método chamado `StringerMethod` que grava uma única linha no console.</span><span class="sxs-lookup"><span data-stu-id="07456-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     <span data-ttu-id="07456-111">Use o comando a seguir para compilar esse código:</span><span class="sxs-lookup"><span data-stu-id="07456-111">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     <span data-ttu-id="07456-112">Especificar o parâmetro *module* com a opção do compilador **/t:** indica que o arquivo deve ser compilado como um módulo em vez de como um assembly.</span><span class="sxs-lookup"><span data-stu-id="07456-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="07456-113">O compilador produz um módulo chamado `Stringer.netmodule`, que pode ser adicionado a um assembly.</span><span class="sxs-lookup"><span data-stu-id="07456-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="07456-114">Compile todos os outros módulos, usando as opções do compilador necessárias para indicar os outros módulos que são referenciados no código.</span><span class="sxs-lookup"><span data-stu-id="07456-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="07456-115">Esta etapa usa a opção do compilador **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="07456-115">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="07456-116">No exemplo a seguir, um módulo de código chamado `Client` tem um método `Main` de ponto de entrada que referencia um método no módulo `Stringer.dll` criado na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="07456-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     <span data-ttu-id="07456-117">Use o comando a seguir para compilar esse código:</span><span class="sxs-lookup"><span data-stu-id="07456-117">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     <span data-ttu-id="07456-118">Especifique a opção **/t:module** porque este módulo será adicionado a um assembly em uma etapa futura.</span><span class="sxs-lookup"><span data-stu-id="07456-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="07456-119">Especifique a opção **/addmodule** porque o código em `Client` referencia um namespace criado pelo código em `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="07456-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="07456-120">O compilador produz um módulo chamado `Client.netmodule` que contém uma referência a outro módulo, `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="07456-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07456-121">Os compiladores C# e Visual Basic dão suporte à criação de assemblies de vários arquivos diretamente usando as duas sintaxes diferentes a seguir.</span><span class="sxs-lookup"><span data-stu-id="07456-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="07456-122">Duas compilações criam um assembly de dois arquivos:</span><span class="sxs-lookup"><span data-stu-id="07456-122">Two compilations create a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   <span data-ttu-id="07456-123">Uma compilação cria um assembly de dois arquivos:</span><span class="sxs-lookup"><span data-stu-id="07456-123">One compilation creates a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  <span data-ttu-id="07456-124">Use o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para criar o arquivo de saída que contém o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="07456-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="07456-125">Esse arquivo contém informações de referência para todos os módulos ou recursos que fazem parte do assembly.</span><span class="sxs-lookup"><span data-stu-id="07456-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="07456-126">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07456-126">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="07456-127">**al** \<*nome do módulo*> \<*nome do módulo*> …</span><span class="sxs-lookup"><span data-stu-id="07456-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="07456-128">**/main:**\<*nome do método*> **/out:**\<*nome de arquivo*> **/target:**\<*tipo de arquivo do assembly*></span><span class="sxs-lookup"><span data-stu-id="07456-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="07456-129">Neste comando, os argumentos *nome do módulo* especificam o nome de cada módulo a ser incluído no assembly.</span><span class="sxs-lookup"><span data-stu-id="07456-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="07456-130">A opção **/main:** especifica o nome do método que é o ponto de entrada do assembly.</span><span class="sxs-lookup"><span data-stu-id="07456-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="07456-131">A opção **/out:** especifica o nome do arquivo de saída, que contém metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="07456-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="07456-132">A opção **/target:** especifica que o assembly está em um arquivo executável de aplicativo de console (.exe), um arquivo executável do Windows (.win) ou um arquivo de biblioteca (.lib).</span><span class="sxs-lookup"><span data-stu-id="07456-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="07456-133">No exemplo a seguir, o Al.exe cria um assembly que é um executável de aplicativo de console chamado `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="07456-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="07456-134">O aplicativo consiste em dois módulos chamados `Client.netmodule` e `Stringer.netmodule` e o arquivo executável chamado `myAssembly.exe,` que contém apenas metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="07456-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata .</span></span> <span data-ttu-id="07456-135">O ponto de entrada do assembly é o método `Main` na classe `MainClientApp`, que está localizado em `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="07456-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="07456-136">Você pode usar o [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar o conteúdo de um assembly ou determinar se um arquivo é um assembly ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="07456-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07456-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07456-137">See Also</span></span>  
 [<span data-ttu-id="07456-138">Criação de assemblies</span><span class="sxs-lookup"><span data-stu-id="07456-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="07456-139">Como exibir o conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="07456-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [<span data-ttu-id="07456-140">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="07456-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="07456-141">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="07456-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
