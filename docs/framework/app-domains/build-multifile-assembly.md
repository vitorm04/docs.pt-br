---
title: 'Como: criar um assembly de vários arquivos'
description: Saiba como compilar (criar) um assembly de multiarquivos no .NET usando o código de exemplo para ilustrar cada etapa no procedimento.
ms.date: 08/20/2019
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
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: a4c298284950ba2989bb73e6d3383b3c4024e6e7
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104953"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="e82b8-103">Como: criar um assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="e82b8-103">How to: Build a multifile assembly</span></span>

<span data-ttu-id="e82b8-104">Este artigo explica como criar um assembly de vários arquivos e fornece código que ilustra cada etapa no procedimento.</span><span class="sxs-lookup"><span data-stu-id="e82b8-104">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="e82b8-105">O IDE do Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="e82b8-105">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="e82b8-106">Se quiser criar assemblies de vários arquivos, você precisará usar os compiladores de linha de comando ou Visual Studio com o Visual C++.</span><span class="sxs-lookup"><span data-stu-id="e82b8-106">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="e82b8-107">Os assemblies de multiarquivo têm suporte apenas pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e82b8-107">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="e82b8-108">Criar um assembly de multiarquivos</span><span class="sxs-lookup"><span data-stu-id="e82b8-108">Create a multifile assembly</span></span>

1. <span data-ttu-id="e82b8-109">Compile todos os arquivos que contêm namespaces referenciados por outros módulos no assembly nos módulos de código.</span><span class="sxs-lookup"><span data-stu-id="e82b8-109">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="e82b8-110">A extensão padrão para módulos de código é *. netmodule*.</span><span class="sxs-lookup"><span data-stu-id="e82b8-110">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="e82b8-111">Por exemplo, digamos que o arquivo `Stringer` tem um namespace chamado `myStringer`, que inclui uma classe chamada `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="e82b8-111">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="e82b8-112">A classe `Stringer` contém um método chamado `StringerMethod` que grava uma única linha no console.</span><span class="sxs-lookup"><span data-stu-id="e82b8-112">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="e82b8-113">Use o comando a seguir para compilar esse código:</span><span class="sxs-lookup"><span data-stu-id="e82b8-113">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="e82b8-114">Especificar o parâmetro *module* com a opção do compilador **/t:** indica que o arquivo deve ser compilado como um módulo em vez de como um assembly.</span><span class="sxs-lookup"><span data-stu-id="e82b8-114">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="e82b8-115">O compilador produz um módulo chamado *Stringer. netmodule*, que pode ser adicionado a um assembly.</span><span class="sxs-lookup"><span data-stu-id="e82b8-115">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="e82b8-116">Compile todos os outros módulos, usando as opções do compilador necessárias para indicar os outros módulos que são referenciados no código.</span><span class="sxs-lookup"><span data-stu-id="e82b8-116">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="e82b8-117">Esta etapa usa a opção do compilador **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="e82b8-117">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="e82b8-118">No exemplo a seguir, um módulo de código chamado *cliente* tem um método de ponto de entrada `Main` que faz referência a um método no módulo *Stringer.dll* criado na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="e82b8-118">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="e82b8-119">Use o comando a seguir para compilar esse código:</span><span class="sxs-lookup"><span data-stu-id="e82b8-119">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="e82b8-120">Especifique a opção **/t:module** porque este módulo será adicionado a um assembly em uma etapa futura.</span><span class="sxs-lookup"><span data-stu-id="e82b8-120">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="e82b8-121">Especifique a opção **/addmodule** porque o código no *cliente* faz referência a um namespace criado pelo código em *Stringer. netmodule*.</span><span class="sxs-lookup"><span data-stu-id="e82b8-121">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="e82b8-122">O compilador produz um módulo chamado *Client. netmodule* que contém uma referência a outro módulo, *Stringer. netmodule*.</span><span class="sxs-lookup"><span data-stu-id="e82b8-122">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e82b8-123">Os compiladores C# e Visual Basic dão suporte à criação de assemblies de vários arquivos diretamente usando as duas sintaxes diferentes a seguir.</span><span class="sxs-lookup"><span data-stu-id="e82b8-123">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="e82b8-124">Duas compilações criam um assembly de dois arquivos:</span><span class="sxs-lookup"><span data-stu-id="e82b8-124">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="e82b8-125">Uma compilação cria um assembly de dois arquivos:</span><span class="sxs-lookup"><span data-stu-id="e82b8-125">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="e82b8-126">Use o [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) para criar o arquivo de saída que contém o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="e82b8-126">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="e82b8-127">Esse arquivo contém informações de referência para todos os módulos ou recursos que fazem parte do assembly.</span><span class="sxs-lookup"><span data-stu-id="e82b8-127">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="e82b8-128">No prompt de comando, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="e82b8-128">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="e82b8-129">**Al** \<*module name*> \<*module name*>...</span><span class="sxs-lookup"><span data-stu-id="e82b8-129">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="e82b8-130">**/Main:** \<*method name*> **/out:** \<*file name*> **/target:**\<*assembly file type*></span><span class="sxs-lookup"><span data-stu-id="e82b8-130">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="e82b8-131">Neste comando, os argumentos *nome do módulo* especificam o nome de cada módulo a ser incluído no assembly.</span><span class="sxs-lookup"><span data-stu-id="e82b8-131">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="e82b8-132">A opção **/main:** especifica o nome do método que é o ponto de entrada do assembly.</span><span class="sxs-lookup"><span data-stu-id="e82b8-132">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="e82b8-133">A opção **/out:** especifica o nome do arquivo de saída, que contém metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="e82b8-133">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="e82b8-134">A opção **/target:** especifica que o assembly é um arquivo executável do aplicativo de console (*. exe*), um arquivo executável do Windows (*. Win*) ou um arquivo de biblioteca (*. lib*).</span><span class="sxs-lookup"><span data-stu-id="e82b8-134">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="e82b8-135">No exemplo a seguir, *Al.exe* cria um assembly que é um executável de aplicativo de console chamado *myAssembly.exe*.</span><span class="sxs-lookup"><span data-stu-id="e82b8-135">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="e82b8-136">O aplicativo consiste em dois módulos chamados *Client. netmodule* e *Stringer. netmodule*, e o arquivo executável chamado *myAssembly.exe*, que contém somente os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="e82b8-136">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="e82b8-137">O ponto de entrada do assembly é o `Main` método na classe `MainClientApp` , que está localizado em *Client.dll*.</span><span class="sxs-lookup"><span data-stu-id="e82b8-137">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="e82b8-138">Você pode usar o [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) para examinar o conteúdo de um assembly ou determinar se um arquivo é um assembly ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="e82b8-138">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="e82b8-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="e82b8-139">See also</span></span>

- [<span data-ttu-id="e82b8-140">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="e82b8-140">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="e82b8-141">Como exibir o conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="e82b8-141">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="e82b8-142">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="e82b8-142">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="e82b8-143">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="e82b8-143">Multifile assemblies</span></span>](multifile-assemblies.md)
