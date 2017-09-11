---
title: "Como compilar um assembly de arquivo único"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1a584e6ded79489e5e33b07d02dde618541c6cc8
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="6d391-102">Como compilar um assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="6d391-102">How to: Build a Single-File Assembly</span></span>
<span data-ttu-id="6d391-103">Um assembly de arquivo único, que é o tipo mais simples de assembly, contém informações sobre o tipo e a implementação, bem como o [manifesto do assembly](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="6d391-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="6d391-104">Você pode usar compiladores de linha de comando ou [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] para criar um assembly de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="6d391-104">You can use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to create a single-file assembly.</span></span> <span data-ttu-id="6d391-105">Por padrão, o compilador cria um arquivo do assembly com uma extensão de .exe.</span><span class="sxs-lookup"><span data-stu-id="6d391-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d391-106">O [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] para C# e Visual Basic pode ser usado para criar assemblies de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="6d391-106">[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="6d391-107">Se quiser criar assemblies de vários arquivos, você precisará usar os compiladores de linha de comando ou [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] para Visual C++.</span><span class="sxs-lookup"><span data-stu-id="6d391-107">If you want to create multifile assemblies, you must use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++.</span></span>  
  
 <span data-ttu-id="6d391-108">Os procedimentos a seguir mostram como criar assemblies de arquivo único usando compiladores de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6d391-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="6d391-109">Para criar um assembly com uma extensão .exe</span><span class="sxs-lookup"><span data-stu-id="6d391-109">To create an assembly with an .exe extension</span></span>  
  
1.  <span data-ttu-id="6d391-110">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="6d391-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="6d391-111">\<*comando do compilador*> \<*nome do módulo*></span><span class="sxs-lookup"><span data-stu-id="6d391-111">\<*compiler command*> \<*module name*></span></span>  
  
     <span data-ttu-id="6d391-112">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="6d391-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="6d391-113">O exemplo a seguir cria um assembly chamado `myCode.exe` de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="6d391-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="6d391-114">Para criar um assembly com uma extensão .exe e especificar o nome do arquivo de saída</span><span class="sxs-lookup"><span data-stu-id="6d391-114">To create an assembly with an .exe extension and specify the output file name</span></span>  
  
1.  <span data-ttu-id="6d391-115">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="6d391-115">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="6d391-116">\<*comando do compilador*> **/out:**\<*nome de arquivo*> \<*nome do módulo*></span><span class="sxs-lookup"><span data-stu-id="6d391-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>  
  
     <span data-ttu-id="6d391-117">Neste comando, o *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código, *nome de arquivo* é o nome de arquivo de saída e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="6d391-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="6d391-118">O exemplo a seguir cria um assembly chamado `myAssembly.exe` de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="6d391-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a><span data-ttu-id="6d391-119">Criando assemblies de biblioteca</span><span class="sxs-lookup"><span data-stu-id="6d391-119">Creating Library Assemblies</span></span>  
 <span data-ttu-id="6d391-120">Um assembly de biblioteca é semelhante a uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="6d391-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="6d391-121">Ele contém tipos que serão referenciados por outros assemblies, mas ele não tem nenhum ponto de entrada para iniciar a execução.</span><span class="sxs-lookup"><span data-stu-id="6d391-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>  
  
#### <a name="to-create-a-library-assembly"></a><span data-ttu-id="6d391-122">Para criar um assembly de biblioteca</span><span class="sxs-lookup"><span data-stu-id="6d391-122">To create a library assembly</span></span>  
  
1.  <span data-ttu-id="6d391-123">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="6d391-123">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="6d391-124">\<*comando do compilador*> **/t:library** \<*nome do módulo*></span><span class="sxs-lookup"><span data-stu-id="6d391-124">\<*compiler command*> **/t:library** \<*module name*></span></span>  
  
     <span data-ttu-id="6d391-125">Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.</span><span class="sxs-lookup"><span data-stu-id="6d391-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="6d391-126">Você também pode usar outras opções do compilador, como a opção **/out:**.</span><span class="sxs-lookup"><span data-stu-id="6d391-126">You can also use other compiler options, such as the **/out:** option.</span></span>  
  
 <span data-ttu-id="6d391-127">O exemplo a seguir cria um assembly de biblioteca chamado `myCodeAssembly.dll` de um módulo de código chamado `myCode`.</span><span class="sxs-lookup"><span data-stu-id="6d391-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d391-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d391-128">See Also</span></span>  
 <span data-ttu-id="6d391-129">[Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="6d391-129">[Creating Assemblies](../../../docs/framework/app-domains/create-assemblies.md) </span></span>  
 <span data-ttu-id="6d391-130">[Assemblies de Vários Arquivos](../../../docs/framework/app-domains/multifile-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="6d391-130">[Multifile Assemblies](../../../docs/framework/app-domains/multifile-assemblies.md) </span></span>  
 <span data-ttu-id="6d391-131">[Como compilar um assembly de vários arquivos](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="6d391-131">[How to: Build a Multifile Assembly](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md) </span></span>  
 [<span data-ttu-id="6d391-132">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="6d391-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)

