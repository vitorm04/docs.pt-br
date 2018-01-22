---
title: Usando o CodeDOM
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
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cd2b8e8ecb0e5d451ebf3c6823144e4a90e0d79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="using-the-codedom"></a><span data-ttu-id="6b95d-102">Usando o CodeDOM</span><span class="sxs-lookup"><span data-stu-id="6b95d-102">Using the CodeDOM</span></span>
<span data-ttu-id="6b95d-103">O CodeDOM fornece tipos que representam muitos dos tipos mais comuns de elementos de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="6b95d-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="6b95d-104">Você pode criar um programa que cria um modelo de código-fonte usando elementos do CodeDOM para montar um grafo de objeto.</span><span class="sxs-lookup"><span data-stu-id="6b95d-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="6b95d-105">Este grafo de objeto pode ser renderizado como código-fonte usando um gerador de código CodeDOM para uma linguagem de programação com suporte.</span><span class="sxs-lookup"><span data-stu-id="6b95d-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="6b95d-106">O CodeDOM também pode ser usado para compilar o código-fonte em um assembly binário.</span><span class="sxs-lookup"><span data-stu-id="6b95d-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="6b95d-107">Alguns usos comuns do CodeDOM incluem:</span><span class="sxs-lookup"><span data-stu-id="6b95d-107">Some common uses for the CodeDOM include:</span></span>  
  
-   <span data-ttu-id="6b95d-108">Geração de código de modelo: gerar código para ASP.NET, proxies de cliente de serviços Web XML, assistentes de código, designers ou outros mecanismos de emissão de código.</span><span class="sxs-lookup"><span data-stu-id="6b95d-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
-   <span data-ttu-id="6b95d-109">Compilação dinâmica: suporte a compilação de código em uma ou várias linguagens.</span><span class="sxs-lookup"><span data-stu-id="6b95d-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="6b95d-110">Compilando um gráfico CodeDOM</span><span class="sxs-lookup"><span data-stu-id="6b95d-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="6b95d-111">O namespace <xref:System.CodeDom> fornece classes para representar a estrutura lógica do código-fonte, independente da sintaxe da linguagem.</span><span class="sxs-lookup"><span data-stu-id="6b95d-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="6b95d-112">A estrutura de um gráfico CodeDOM</span><span class="sxs-lookup"><span data-stu-id="6b95d-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="6b95d-113">A estrutura de um grafo CodeDOM é como uma árvore de contêineres.</span><span class="sxs-lookup"><span data-stu-id="6b95d-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="6b95d-114">O contêiner mais alto de cada grafo CodeDOM compilável, a raiz, é um <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="6b95d-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="6b95d-115">Cada elemento de seu modelo de código-fonte deve ser vinculado ao grafo por meio de uma propriedade de um <xref:System.CodeDom.CodeObject> no grafo.</span><span class="sxs-lookup"><span data-stu-id="6b95d-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="6b95d-116">Criando um modelo de código-fonte para um programa Olá, Mundo de exemplo</span><span class="sxs-lookup"><span data-stu-id="6b95d-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="6b95d-117">A instrução passo a passo a seguir fornece um exemplo de como criar um grafo de objeto CodeDOM que representa o código de um aplicativo Olá, Mundo simples.</span><span class="sxs-lookup"><span data-stu-id="6b95d-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="6b95d-118">Para ver o código-fonte completo deste exemplo de código, consulte o tópico <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b95d-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="6b95d-119">Criando uma unidade de compilação</span><span class="sxs-lookup"><span data-stu-id="6b95d-119">Creating a compile unit</span></span>  
 <span data-ttu-id="6b95d-120">O CodeDOM define um objeto chamado de <xref:System.CodeDom.CodeCompileUnit>, que pode fazer referência a um grafo de objeto do CodeDOM que modela o código-fonte a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="6b95d-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="6b95d-121">Um **CodeCompileUnit** tem propriedades para armazenar referências aos atributos, namespaces e assemblies.</span><span class="sxs-lookup"><span data-stu-id="6b95d-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="6b95d-122">Os provedores do CodeDom que derivam da classe <xref:System.CodeDom.Compiler.CodeDomProvider> contém métodos que processam o grafo do objeto referenciado por um **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="6b95d-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="6b95d-123">Para criar um grafo de objeto para um aplicativo simples, você deve montar o modelo de código-fonte e referenciá-lo de um **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="6b95d-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="6b95d-124">Você pode criar uma nova unidade de compilação com a sintaxe mostrada neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="6b95d-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="6b95d-125">Um <xref:System.CodeDom.CodeSnippetCompileUnit> pode conter uma seção de código-fonte que já está na linguagem de destino, mas não pode ser renderizado para outra linguagem.</span><span class="sxs-lookup"><span data-stu-id="6b95d-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="6b95d-126">Definindo um namespace</span><span class="sxs-lookup"><span data-stu-id="6b95d-126">Defining a namespace</span></span>  
 <span data-ttu-id="6b95d-127">Para definir um namespace, crie um <xref:System.CodeDom.CodeNamespace> e atribua um nome para ele usando o construtor apropriado ou definindo sua propriedade **Nome**.</span><span class="sxs-lookup"><span data-stu-id="6b95d-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="6b95d-128">Importando um namespace</span><span class="sxs-lookup"><span data-stu-id="6b95d-128">Importing a namespace</span></span>  
 <span data-ttu-id="6b95d-129">Para adicionar uma diretiva de importação do namespace ao namespace, adicione um <xref:System.CodeDom.CodeNamespaceImport> que indica o namespace a ser importado para a coleção **CodeNamespace.Imports**.</span><span class="sxs-lookup"><span data-stu-id="6b95d-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="6b95d-130">O código a seguir adiciona uma importação para o namespace **System** à coleção **Importações** de um **CodeNamespace** chamado `samples`:</span><span class="sxs-lookup"><span data-stu-id="6b95d-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="6b95d-131">Vincular elementos de código ao grafo do objeto</span><span class="sxs-lookup"><span data-stu-id="6b95d-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="6b95d-132">Todos os elementos de código que formam um grafo CodeDOM devem ser vinculados ao <xref:System.CodeDom.CodeCompileUnit>, que é o elemento raiz da árvore por uma série de referências entre os elementos referenciados diretamente das propriedades do objeto raiz do grafo.</span><span class="sxs-lookup"><span data-stu-id="6b95d-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="6b95d-133">Defina um objeto como uma propriedade de um objeto de contêiner para estabelecer uma referência do objeto de contêiner.</span><span class="sxs-lookup"><span data-stu-id="6b95d-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="6b95d-134">A instrução a seguir adiciona o `samples` **CodeNamespace** à propriedade da coleção **Namespaces** da raiz **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="6b95d-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="6b95d-135">Definindo um tipo</span><span class="sxs-lookup"><span data-stu-id="6b95d-135">Defining a type</span></span>  
 <span data-ttu-id="6b95d-136">Para declarar uma classe, estrutura, interface ou enumeração usando o CodeDOM, crie um novo <xref:System.CodeDom.CodeTypeDeclaration> e atribua um nome.</span><span class="sxs-lookup"><span data-stu-id="6b95d-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="6b95d-137">O exemplo a seguir demonstra isso usando uma sobrecarga de construtor para definir a propriedade **Nome**:</span><span class="sxs-lookup"><span data-stu-id="6b95d-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="6b95d-138">Para adicionar um tipo a um namespace, adicione um <xref:System.CodeDom.CodeTypeDeclaration> que representa o tipo a ser adicionado para o namespace à coleção **Tipos** de um **CodeNamespace**.</span><span class="sxs-lookup"><span data-stu-id="6b95d-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="6b95d-139">O exemplo a seguir demonstra como adicionar uma classe denominada `class1` para um **CodeNamespace** chamado `samples`:</span><span class="sxs-lookup"><span data-stu-id="6b95d-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="6b95d-140">Adicionar membros de classe a uma classe</span><span class="sxs-lookup"><span data-stu-id="6b95d-140">Adding class members to a class</span></span>  
 <span data-ttu-id="6b95d-141">O namespace <xref:System.CodeDom> fornece uma variedade de elementos que podem ser usados para representar os membros de classe.</span><span class="sxs-lookup"><span data-stu-id="6b95d-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="6b95d-142">Cada membro de classe pode ser adicionado à coleção **Membros** de um <xref:System.CodeDom.CodeTypeDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="6b95d-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="6b95d-143">Definindo um método de ponto de entrada de código para um executável</span><span class="sxs-lookup"><span data-stu-id="6b95d-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="6b95d-144">Se você estiver compilando código para um programa executável, será necessário indicar o ponto de entrada de um programa criando um <xref:System.CodeDom.CodeEntryPointMethod> para representar o método no qual a execução do programa deve começar.</span><span class="sxs-lookup"><span data-stu-id="6b95d-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="6b95d-145">O exemplo a seguir demonstra como definir um método de ponto de entrada que contém um <xref:System.CodeDom.CodeMethodInvokeExpression> que chama **System.Console.WriteLine** para imprimir “Hello World!”:</span><span class="sxs-lookup"><span data-stu-id="6b95d-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="6b95d-146">A instrução a seguir adiciona o método de ponto de entrada denominado `Start` à coleção **Membros** de `class1`:</span><span class="sxs-lookup"><span data-stu-id="6b95d-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="6b95d-147">Agora o <xref:System.CodeDom.CodeCompileUnit> chamado `compileUnit` contém o grafo CodeDOM para um programa Olá, Mundo simples.</span><span class="sxs-lookup"><span data-stu-id="6b95d-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="6b95d-148">Para obter informações sobre como gerar e compilar o código de um grafo CodeDOM, consulte [Gerando código-fonte e compilando um programa de um grafo CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="6b95d-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="6b95d-149">Mais informações sobre a compilação de um grafo CodeDOM</span><span class="sxs-lookup"><span data-stu-id="6b95d-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="6b95d-150">O CodeDOM dá suporte a muitos tipos comuns de elementos de código encontrados em linguagens de programação que dão suporte ao Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="6b95d-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="6b95d-151">O CodeDOM não foi projetado para fornecer elementos para representar todos os recursos de linguagem de programação possíveis.</span><span class="sxs-lookup"><span data-stu-id="6b95d-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="6b95d-152">Código que não pode ser representado facilmente com elementos do CodeDOM pode ser encapsulado em um <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember> ou <xref:System.CodeDom.CodeSnippetCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="6b95d-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="6b95d-153">No entanto, trechos de código não podem ser convertidos para outras linguagens automaticamente pelo CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="6b95d-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="6b95d-154">Para obter a documentação para cada um dos tipos do CodeDOM, consulte a documentação de referência para o namespace <xref:System.CodeDom>.</span><span class="sxs-lookup"><span data-stu-id="6b95d-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="6b95d-155">Para uma verificação rápida para localizar o elemento de CodeDOM que representa um tipo específico de elemento de código, consulte a [Referência rápida do CodeDOM](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span><span class="sxs-lookup"><span data-stu-id="6b95d-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span></span>
