---
title: Geração e compilação de código-fonte dinâmico
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90b4214e244bc1f9c5f8e71782e604bd6c7b619
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582587"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="5ff77-102">Geração e compilação de código-fonte dinâmico</span><span class="sxs-lookup"><span data-stu-id="5ff77-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="5ff77-103">O .NET Framework inclui um mecanismo chamado CodeDOM (Modelo de Objeto do Documento de Código) que permite aos desenvolvedores de programas que emitem o código-fonte gerar o código-fonte em várias linguagens de programação no tempo de execução com base em um único modelo que representa o código a ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="5ff77-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="5ff77-104">Para representar o código-fonte, os elementos do CodeDOM são vinculados uns aos outros para formar uma estrutura de dados conhecida como um grafo CodeDOM, que modela a estrutura de parte do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="5ff77-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="5ff77-105">O namespace `System.CodeDom` define tipos que podem representam a estrutura lógica do código-fonte, independente de uma linguagem de programação específica.</span><span class="sxs-lookup"><span data-stu-id="5ff77-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="5ff77-106">O namespace `System.CodeDom.Compiler` define tipos para gerar código-fonte de grafos CodeDOM e gerenciar a compilação do código-fonte em linguagens com suporte.</span><span class="sxs-lookup"><span data-stu-id="5ff77-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="5ff77-107">Fornecedores de compilador ou desenvolvedores podem estender o conjunto de idiomas com suporte.</span><span class="sxs-lookup"><span data-stu-id="5ff77-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="5ff77-108">A modelagem de código-fonte independente de linguagem pode ser útil quando um programa precisa gerar código-fonte para um modelo de programa em várias linguagens ou para uma linguagem de destino incerta.</span><span class="sxs-lookup"><span data-stu-id="5ff77-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="5ff77-109">Por exemplo, alguns designers usam CodeDOM como uma interface da abstração de linguagem para produzir código-fonte na linguagem de programação correta, caso haja suporte para a linguagem no CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="5ff77-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="5ff77-110">O .NET Framework inclui geradores e compiladores de código para <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider> e <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="5ff77-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ff77-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5ff77-111">In This Section</span></span>  
 [<span data-ttu-id="5ff77-112">Usando o CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5ff77-112">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 <span data-ttu-id="5ff77-113">Descreve os usos comuns e demonstra como criar um grafo de objeto simples usando o CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="5ff77-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="5ff77-114">Gerando e código-fonte e compilando um programa de um gráfico CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5ff77-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="5ff77-115">Descreve como gerar o código-fonte e compilar o código gerado com um compilador externo usando classes definidas no namespace `System.CodeDom.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="5ff77-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="5ff77-116">Como criar um arquivo de documentação XML usando CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5ff77-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="5ff77-117">Descreve como usar CodeDOM para gerar código com comentários de documentação XML e compilar o código gerado para que ele cria a saída de documentação XML.</span><span class="sxs-lookup"><span data-stu-id="5ff77-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="5ff77-118">Como criar uma classe usando o CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5ff77-118">How to: Create a Class Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="5ff77-119">Descreve como usar CodeDOM para gerar uma classe que contém campos, propriedades, um método, um construtor e um ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="5ff77-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5ff77-120">Referência</span><span class="sxs-lookup"><span data-stu-id="5ff77-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="5ff77-121">Define os elementos que representam os elementos de código em linguagens de programação que usam o Common Language Runtime como destino.</span><span class="sxs-lookup"><span data-stu-id="5ff77-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="5ff77-122">Define as interfaces para gerar e compilar o código no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5ff77-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ff77-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="5ff77-123">Related Sections</span></span>  
 [<span data-ttu-id="5ff77-124">Referência rápida do CodeDOM</span><span class="sxs-lookup"><span data-stu-id="5ff77-124">CodeDOM Quick Reference</span></span>](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 <span data-ttu-id="5ff77-125">Fornece uma maneira rápida para os desenvolvedores localizarem os elementos do CodeDOM que representam os elementos de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="5ff77-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
