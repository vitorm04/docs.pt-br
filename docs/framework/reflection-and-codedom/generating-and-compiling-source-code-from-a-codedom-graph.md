---
title: "Gerando e compilando código-fonte de um gráfico CodeDOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55ba7c1b9dd7e8c912903fb9827e0073a8329abb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="24c73-102">Gerando e compilando código-fonte de um gráfico CodeDOM</span><span class="sxs-lookup"><span data-stu-id="24c73-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="24c73-103">O namespace <xref:System.CodeDom.Compiler> fornece interfaces para geração de código-fonte de grafos de objeto CodeDOM e para o gerenciamento da compilação com compiladores com suporte.</span><span class="sxs-lookup"><span data-stu-id="24c73-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="24c73-104">Um provedor de código pode produzir código-fonte em uma linguagem de programação específica acordo com um grafo CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="24c73-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="24c73-105">Uma classe que deriva de <xref:System.CodeDom.Compiler.CodeDomProvider> normalmente pode fornecer métodos para gerar e compilar o código para a linguagem à qual o provedor dá suporte.</span><span class="sxs-lookup"><span data-stu-id="24c73-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="24c73-106">Usando um provedor de código CodeDOM para gerar código-fonte</span><span class="sxs-lookup"><span data-stu-id="24c73-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="24c73-107">Para gerar o código-fonte em uma determinada linguagem, você precisa de um grafo CodeDOM que representa a estrutura do código-fonte a ser gerada.</span><span class="sxs-lookup"><span data-stu-id="24c73-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="24c73-108">O exemplo a seguir demonstra como criar uma instância de um <xref:Microsoft.CSharp.CSharpCodeProvider>:</span><span class="sxs-lookup"><span data-stu-id="24c73-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="24c73-109">O gráfico para geração de código geralmente está contido em um <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="24c73-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="24c73-110">Para gerar o código para uma **CodeCompileUnit** que contém um grafo CodeDOM, chame o método <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> do provedor de código.</span><span class="sxs-lookup"><span data-stu-id="24c73-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="24c73-111">Esse método tem um parâmetro para um <xref:System.IO.TextWriter> que ele usa para gerar o código-fonte, portanto, às vezes é necessário criar primeiro um **TextWriter** que pode ser gravado.</span><span class="sxs-lookup"><span data-stu-id="24c73-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="24c73-112">O exemplo a seguir demonstra o código de geração de um **CodeCompileUnit** e a gravação do código-fonte gerado em um arquivo chamado HelloWorld.cs.</span><span class="sxs-lookup"><span data-stu-id="24c73-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="24c73-113">Usando um provedor de código CodeDOM para compilar assemblies</span><span class="sxs-lookup"><span data-stu-id="24c73-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="24c73-114">**Invocando a compilação**</span><span class="sxs-lookup"><span data-stu-id="24c73-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="24c73-115">Para compilar um assembly usando um provedor de CodeDom, você deve ter o código-fonte para compilar em uma linguagem para a qual tenha um compilador ou um grafo CodeDOM do qual o código-fonte pode ser gerado.</span><span class="sxs-lookup"><span data-stu-id="24c73-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="24c73-116">Se você estiver compilando de um grafo CodeDOM, passe o <xref:System.CodeDom.CodeCompileUnit> que contém o grafo para o método <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> do provedor de código.</span><span class="sxs-lookup"><span data-stu-id="24c73-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="24c73-117">Se você tiver um arquivo de código-fonte em uma linguagem que o compilador compreende, passe o nome do arquivo que contém o código-fonte para o método <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> do provedor de CodeDom.</span><span class="sxs-lookup"><span data-stu-id="24c73-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="24c73-118">Você também pode passar uma cadeia de caracteres que contém o código-fonte em uma linguagem que o compilador compreende para o método <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> do provedor de CodeDom.</span><span class="sxs-lookup"><span data-stu-id="24c73-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="24c73-119">**Configurando parâmetros de compilação**</span><span class="sxs-lookup"><span data-stu-id="24c73-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="24c73-120">Todos os métodos padrão de invocar a compilação de um provedor de CodeDom têm um parâmetro do tipo <xref:System.CodeDom.Compiler.CompilerParameters> que indica as opções a serem usadas para compilação.</span><span class="sxs-lookup"><span data-stu-id="24c73-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="24c73-121">Você pode especificar um nome de arquivo do assembly de saída na propriedade <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> de **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="24c73-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="24c73-122">Caso contrário, um nome de arquivo de saída padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="24c73-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="24c73-123">Por padrão, um novo **CompilerParameters** é inicializado com sua propriedade <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> definida como **false**.</span><span class="sxs-lookup"><span data-stu-id="24c73-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="24c73-124">Se estiver compilando um programa executável, você deverá definir a propriedade **GenerateExecutable** como **true**.</span><span class="sxs-lookup"><span data-stu-id="24c73-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="24c73-125">Quando o **GenerateExecutable** estiver definido como **false**, o compilador gerará uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="24c73-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="24c73-126">Se você estiver compilando um executável de um grafo CodeDOM, um <xref:System.CodeDom.CodeEntryPointMethod> deverá ser definido no grafo.</span><span class="sxs-lookup"><span data-stu-id="24c73-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="24c73-127">Se houver vários pontos de entrada de código, poderá ser necessário definir a propriedade <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> de **CompilerParameters** para o nome da classe que define o ponto de entrada a ser usado.</span><span class="sxs-lookup"><span data-stu-id="24c73-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="24c73-128">Para incluir informações de depuração em um executável gerado, defina a propriedade <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> como **true**.</span><span class="sxs-lookup"><span data-stu-id="24c73-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="24c73-129">Se seu projeto fizer referência a quaisquer assemblies, você precisará especificar os nomes de assembly como itens em uma <xref:System.Collections.Specialized.StringCollection> como a propriedade <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> de **CompilerParameters** usado ao invocar a compilação.</span><span class="sxs-lookup"><span data-stu-id="24c73-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="24c73-130">Você pode compilar um assembly que é gravado na memória e não no disco definindo a propriedade <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> como **true**.</span><span class="sxs-lookup"><span data-stu-id="24c73-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="24c73-131">Quando um assembly é gerado na memória, seu código pode obter uma referência para o assembly gerado da propriedade <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> de um <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="24c73-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="24c73-132">Se um assembly estiver gravado em disco, você poderá obter o caminho para o assembly gerado na propriedade <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> de um **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="24c73-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="24c73-133">Para especificar uma cadeia de caracteres de argumentos de linha de comando personalizados a ser usada ao invocar o processo de compilação, defina a cadeia de caracteres na propriedade <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="24c73-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="24c73-134">Se um token de segurança do Win32 for necessário para invocar o processo do compilador, especifique o token na propriedade <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A>.</span><span class="sxs-lookup"><span data-stu-id="24c73-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="24c73-135">Para vincular um arquivo de recurso Win32 no assembly compilado, especifique o nome do arquivo de recurso Win32 na propriedade <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A>.</span><span class="sxs-lookup"><span data-stu-id="24c73-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="24c73-136">Para especificar um nível de aviso no qual interromper a compilação, defina a propriedade <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> como um inteiro que representa o nível de aviso no qual interromper a compilação.</span><span class="sxs-lookup"><span data-stu-id="24c73-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="24c73-137">Você também pode configurar o compilador para interromper a compilação se forem encontrados avisos definindo a propriedade <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> como **true**.</span><span class="sxs-lookup"><span data-stu-id="24c73-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="24c73-138">O exemplo de código a seguir demonstra a compilação de um arquivo de origem usando um provedor CodeDom derivado da classe <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="24c73-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="24c73-139">Linguagens com suporte inicial</span><span class="sxs-lookup"><span data-stu-id="24c73-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="24c73-140">O .NET Framework fornece compiladores de código e geradores de código para as seguintes linguagens: C#, Visual Basic, C++ e JScript.</span><span class="sxs-lookup"><span data-stu-id="24c73-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="24c73-141">O suporte do CodeDOM pode ser estendido a outras linguagens implementando geradores de código e compiladores de código específicos da linguagem.</span><span class="sxs-lookup"><span data-stu-id="24c73-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c73-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24c73-142">See Also</span></span>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="24c73-143">[Dynamic Source Code Generation and Compilation](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md) (Compilação e geração de código-fonte dinâmico)</span><span class="sxs-lookup"><span data-stu-id="24c73-143">[Dynamic Source Code Generation and Compilation](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)</span></span>  
 [<span data-ttu-id="24c73-144">Referência rápida do CodeDOM</span><span class="sxs-lookup"><span data-stu-id="24c73-144">CodeDOM Quick Reference</span></span>](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
