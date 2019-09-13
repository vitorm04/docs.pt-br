---
title: 'Como: Criar uma classe usando o CodeDOM'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3f7363ec5f8c954dd55a9500dcf8f2e302424f
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894894"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="d9965-102">Como: Criar uma classe usando o CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d9965-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="d9965-103">Os procedimentos a seguir ilustram como criar e compilar um grafo CodeDOM que gera uma classe que contém dois campos, três propriedades, um método, um construtor e um ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="d9965-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="d9965-104">Crie um aplicativo de console que usará o código CodeDOM para gerar o código-fonte para uma classe.</span><span class="sxs-lookup"><span data-stu-id="d9965-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="d9965-105">Neste exemplo, a classe de geração é nomeada `Sample` e o código gerado é uma classe chamada `CodeDOMCreatedClass` em um arquivo chamado SampleCode.</span><span class="sxs-lookup"><span data-stu-id="d9965-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="d9965-106">Na classe de geração, inicialize o grafo CodeDOM e use os métodos CodeCOM para definir os membros, o construtor e o ponto de entrada (método `Main`) da classe gerada.</span><span class="sxs-lookup"><span data-stu-id="d9965-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="d9965-107">Neste exemplo, a classe gerada tem dois campos, três propriedades, um construtor, um método e um método `Main`.</span><span class="sxs-lookup"><span data-stu-id="d9965-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="d9965-108">Na classe de geração, crie um provedor de código de específico da linguagem e chame seu método <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> para gerar o código do grafo.</span><span class="sxs-lookup"><span data-stu-id="d9965-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="d9965-109">Compile e execute o aplicativo para gerar o código.</span><span class="sxs-lookup"><span data-stu-id="d9965-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="d9965-110">Neste exemplo, o código gerado está em um arquivo chamado SampleCode.</span><span class="sxs-lookup"><span data-stu-id="d9965-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="d9965-111">Compilar e executar esse código para ver a saída de exemplo.</span><span class="sxs-lookup"><span data-stu-id="d9965-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="d9965-112">Para criar o aplicativo que executará o código CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d9965-112">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="d9965-113">Crie uma classe de aplicativo de console para conter o código CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="d9965-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="d9965-114">Defina os campos globais que devem ser usados na classe para referenciar o assembly (<xref:System.CodeDom.CodeCompileUnit>) e classes (<xref:System.CodeDom.CodeTypeDeclaration>), especifique o nome do arquivo de origem gerado e declare o método `Main`.</span><span class="sxs-lookup"><span data-stu-id="d9965-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="d9965-115">Para inicializar o grafo CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d9965-115">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d9965-116">No construtor para a classe de aplicativo de console, inicialize o assembly e a classe e adicione as declarações apropriadas para o grafo CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="d9965-116">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="d9965-117">Para adicionar membros ao grafo CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d9965-117">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d9965-118">Adicione campos ao grafo CodeDOM adicionando objetos <xref:System.CodeDom.CodeMemberField> para a propriedade <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> da classe.</span><span class="sxs-lookup"><span data-stu-id="d9965-118">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="d9965-119">Adicione propriedades ao grafo CodeDOM adicionando objetos <xref:System.CodeDom.CodeMemberProperty> à propriedade <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> da classe.</span><span class="sxs-lookup"><span data-stu-id="d9965-119">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="d9965-120">Adicione um método ao grafo CodeDOM adicionando um objeto <xref:System.CodeDom.CodeMemberMethod> à propriedade <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> da classe.</span><span class="sxs-lookup"><span data-stu-id="d9965-120">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="d9965-121">Adicione um construtor ao grafo CodeDOM adicionando um objeto <xref:System.CodeDom.CodeConstructor> à propriedade <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> da classe.</span><span class="sxs-lookup"><span data-stu-id="d9965-121">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="d9965-122">Adicione um ponto de entrada ao grafo CodeDOM adicionando um objeto <xref:System.CodeDom.CodeEntryPointMethod> à propriedade <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> da classe.</span><span class="sxs-lookup"><span data-stu-id="d9965-122">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="d9965-123">Para gerar o código do grafo CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d9965-123">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="d9965-124">Gere o código-fonte do grafo CodeDOM chamando o método <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9965-124">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="d9965-125">Para criar o gráfico e gerar o código</span><span class="sxs-lookup"><span data-stu-id="d9965-125">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="d9965-126">Adicione os métodos criados nas etapas anteriores para o método `Main` definido na primeira etapa.</span><span class="sxs-lookup"><span data-stu-id="d9965-126">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="d9965-127">Compile e execute a classe de geração.</span><span class="sxs-lookup"><span data-stu-id="d9965-127">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9965-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9965-128">Example</span></span>  
 <span data-ttu-id="d9965-129">O exemplo de código a seguir mostra o código das etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="d9965-129">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="d9965-130">Quando o exemplo anterior é compilado e executado, ele produz o seguinte código-fonte.</span><span class="sxs-lookup"><span data-stu-id="d9965-130">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="d9965-131">O código-fonte gerado produz a seguinte saída quando compilado e executado.</span><span class="sxs-lookup"><span data-stu-id="d9965-131">The generated source code produces the following output when compiled and executed.</span></span>  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d9965-132">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d9965-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="d9965-133">Este exemplo de código requer a permissão `FullTrust` definida para ser executado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d9965-133">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9965-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9965-134">See also</span></span>

- [<span data-ttu-id="d9965-135">Usando o CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d9965-135">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)
- [<span data-ttu-id="d9965-136">Gerando e compilando código-fonte de um gráfico CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d9965-136">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
