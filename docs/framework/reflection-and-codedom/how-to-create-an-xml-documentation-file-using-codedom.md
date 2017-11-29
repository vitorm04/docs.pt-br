---
title: "Como criar um arquivo de documentação XML usando CodeDOM"
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
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7ce95b1c4f33ed500eabf3f9c7a7ac01a3a08e03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="26560-102">Como criar um arquivo de documentação XML usando CodeDOM</span><span class="sxs-lookup"><span data-stu-id="26560-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="26560-103">O CodeDOM pode ser usado para criar o código que gera a documentação XML.</span><span class="sxs-lookup"><span data-stu-id="26560-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="26560-104">O processo envolve a criação do grafo CodeDOM que contém os comentários de documentação XML, a geração do código e a compilação do código gerado com a opção do compilador que cria a saída de documentação XML.</span><span class="sxs-lookup"><span data-stu-id="26560-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="26560-105">Para criar um grafo CodeDOM que contém comentários de documentação XML</span><span class="sxs-lookup"><span data-stu-id="26560-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1.  <span data-ttu-id="26560-106">Crie um <xref:System.CodeDom.CodeCompileUnit> que contém o grafo CodeDOM para o aplicativo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="26560-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2.  <span data-ttu-id="26560-107">Use o construtor <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> com o parâmetro `docComment` definido como `true` para criar o texto e os elementos de comentário da documentação XML.</span><span class="sxs-lookup"><span data-stu-id="26560-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="26560-108">Para gerar o código do CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="26560-108">To generate the code from the CodeCompileUnit</span></span>  
  
1.  <span data-ttu-id="26560-109">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> para gerar o código e criar um arquivo de origem a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="26560-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="26560-110">Para compilar o código e gerar o arquivo de documentação</span><span class="sxs-lookup"><span data-stu-id="26560-110">To compile the code and generate the documentation file</span></span>  
  
1.  <span data-ttu-id="26560-111">Adicione a opção do compilador **/doc** à propriedade <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> de um objeto <xref:System.CodeDom.Compiler.CompilerParameters> e passe o objeto para o método <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> para criar o arquivo de documentação XML quando o código é compilado.</span><span class="sxs-lookup"><span data-stu-id="26560-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="26560-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26560-112">Example</span></span>  
 <span data-ttu-id="26560-113">O exemplo de código a seguir cria um grafo CodeDOM com comentários de documentação, gera um arquivo de código do grafo e compila o arquivo e cria um arquivo de documentação XML associado.</span><span class="sxs-lookup"><span data-stu-id="26560-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="26560-114">O exemplo de código cria a seguinte documentação XML no arquivo HelloWorldDoc.xml.</span><span class="sxs-lookup"><span data-stu-id="26560-114">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
```xml  
<?xml version="1.0" ?>   
<doc>  
  <assembly>  
    <name>HelloWorld</name>   
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.   
        <seealso cref="M:Samples.Class1.Main" />   
      </summary>  
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.   
        <para>Add a new paragraph to the description.</para>   
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26560-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="26560-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="26560-116">Este exemplo de código requer a permissão `FullTrust` definida para ser executado com êxito.</span><span class="sxs-lookup"><span data-stu-id="26560-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26560-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26560-117">See Also</span></span>  
 [<span data-ttu-id="26560-118">Documentando o Código com XML</span><span class="sxs-lookup"><span data-stu-id="26560-118">Documenting Your Code with XML</span></span>](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="26560-119">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="26560-119">XML Documentation Comments</span></span>](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="26560-120">Documentação XML</span><span class="sxs-lookup"><span data-stu-id="26560-120">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)
