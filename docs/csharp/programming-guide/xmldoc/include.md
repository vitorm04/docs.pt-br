---
title: '&lt;include&gt; (Guia de Programação em C#)'
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 854c8b61fa8164bccfc9451f2f163dab4a56388f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697731"
---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="fd823-102">&lt;include&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fd823-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="fd823-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd823-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd823-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd823-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="fd823-105">O nome do arquivo XML que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="fd823-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="fd823-106">O nome do arquivo pode ser qualificado com um caminho relativo ao arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="fd823-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="fd823-107">Coloque `filename` entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="fd823-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="fd823-108">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="fd823-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="fd823-109">Coloque o caminho entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="fd823-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="fd823-110">O especificador de nome na marca que precede os comentários; `name` terá um `id`.</span><span class="sxs-lookup"><span data-stu-id="fd823-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="fd823-111">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="fd823-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="fd823-112">Coloque a ID entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="fd823-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd823-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd823-113">Remarks</span></span>  
 <span data-ttu-id="fd823-114">A marca \<include> permite consultar comentários em outro arquivo que descrevem os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="fd823-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="fd823-115">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="fd823-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="fd823-116">Colocando a documentação em um arquivo separado, é possível aplicar o controle do código-fonte à documentação separadamente do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="fd823-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="fd823-117">Uma pessoa pode fazer o check-out do arquivo de código-fonte e outra pessoa pode fazer o check-out do arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="fd823-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="fd823-118">A marca \<include> usa a sintaxe XML XPath.</span><span class="sxs-lookup"><span data-stu-id="fd823-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="fd823-119">Consulte a documentação do XPath para obter maneiras de personalizar o uso de \<include>.</span><span class="sxs-lookup"><span data-stu-id="fd823-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd823-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd823-120">Example</span></span>  
 <span data-ttu-id="fd823-121">Este é um exemplo de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="fd823-121">This is a multifile example.</span></span> <span data-ttu-id="fd823-122">O primeiro arquivo, que usa \<include>, é listado abaixo:</span><span class="sxs-lookup"><span data-stu-id="fd823-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 <span data-ttu-id="fd823-123">O segundo arquivo, xml_include_tag.doc, contém os comentários de documentação a seguir:</span><span class="sxs-lookup"><span data-stu-id="fd823-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a><span data-ttu-id="fd823-124">Saída do Programa</span><span class="sxs-lookup"><span data-stu-id="fd823-124">Program Output</span></span>  
 <span data-ttu-id="fd823-125">A seguinte saída é gerada quando você compila as classes Test e Test2 com a seguinte linha de comando: `/doc:DocFileName.xml.` No Visual Studio, especifique a opção de comentários de documentos XML no painel Compilar do Designer de Projeto.</span><span class="sxs-lookup"><span data-stu-id="fd823-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="fd823-126">Quando o compilador C# encontrar a marca \<include>, ele pesquisará os comentários da documentação em xml_include_tag.doc, em vez de no arquivo de origem atual.</span><span class="sxs-lookup"><span data-stu-id="fd823-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="fd823-127">O compilador, então, gera DocFileName.xml e esse é o arquivo consumido pelas ferramentas de documentação como [Sandcastle](https://github.com/EWSoftware/SHFB) para gerar a documentação final.</span><span class="sxs-lookup"><span data-stu-id="fd823-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a><span data-ttu-id="fd823-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd823-128">See Also</span></span>

- [<span data-ttu-id="fd823-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fd823-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fd823-130">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="fd823-130">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
