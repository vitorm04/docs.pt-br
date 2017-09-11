---
title: "&lt;include&gt; (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- include
- <include>
dev_langs:
- CSharp
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: df0438dd742db802bb0f935d840006236d5d9bf9
ms.openlocfilehash: 0cabcc25c4e35027c600e4af2bccfad7f9db1514
ms.contentlocale: pt-br
ms.lasthandoff: 08/29/2017

---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="03553-102">&lt;include&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="03553-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="03553-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03553-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03553-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03553-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="03553-105">O nome do arquivo XML que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="03553-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="03553-106">O nome do arquivo pode ser qualificado com um caminho.</span><span class="sxs-lookup"><span data-stu-id="03553-106">The file name can be qualified with a path.</span></span> <span data-ttu-id="03553-107">Coloque `filename` entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="03553-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="03553-108">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="03553-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="03553-109">Coloque o caminho entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="03553-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="03553-110">O especificador de nome na marca que precede os comentários; `name` terá um `id`.</span><span class="sxs-lookup"><span data-stu-id="03553-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="03553-111">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="03553-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="03553-112">Coloque a ID entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="03553-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03553-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="03553-113">Remarks</span></span>  
 <span data-ttu-id="03553-114">A marca \<include> permite consultar comentários em outro arquivo que descrevem os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="03553-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="03553-115">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="03553-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="03553-116">Colocando a documentação em um arquivo separado, é possível aplicar o controle do código-fonte à documentação separadamente do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="03553-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="03553-117">Uma pessoa pode fazer o check-out do arquivo de código-fonte e outra pessoa pode fazer o check-out do arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="03553-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="03553-118">A marca \<include> usa a sintaxe XML XPath.</span><span class="sxs-lookup"><span data-stu-id="03553-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="03553-119">Consulte a documentação do XPath para obter maneiras de personalizar o uso de \<include>.</span><span class="sxs-lookup"><span data-stu-id="03553-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03553-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03553-120">Example</span></span>  
 <span data-ttu-id="03553-121">Este é um exemplo de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="03553-121">This is a multifile example.</span></span> <span data-ttu-id="03553-122">O primeiro arquivo, que usa \<include>, é listado abaixo:</span><span class="sxs-lookup"><span data-stu-id="03553-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 <span data-ttu-id="03553-123">[!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="03553-123">[!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]</span></span>  
  
 <span data-ttu-id="03553-124">O segundo arquivo, xml_include_tag.doc, contém os comentários de documentação a seguir:</span><span class="sxs-lookup"><span data-stu-id="03553-124">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
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
  
## <a name="program-output"></a><span data-ttu-id="03553-125">Saída do Programa</span><span class="sxs-lookup"><span data-stu-id="03553-125">Program Output</span></span>  
 <span data-ttu-id="03553-126">A seguinte saída é gerada quando você compila as classes Test e Test2 com a seguinte linha de comando: `/doc:DocFileName.xml.` No Visual Studio, especifique a opção de comentários de documentos XML no painel Compilar do Designer de Projeto.</span><span class="sxs-lookup"><span data-stu-id="03553-126">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="03553-127">Quando o compilador C# encontrar a marca \<include>, ele pesquisará os comentários da documentação em xml_include_tag.doc, em vez de no arquivo de origem atual.</span><span class="sxs-lookup"><span data-stu-id="03553-127">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="03553-128">O compilador, então, gera DocFileName.xml e esse é o arquivo consumido pelas ferramentas de documentação como [Sandcastle](https://github.com/EWSoftware/SHFB) para gerar a documentação final.</span><span class="sxs-lookup"><span data-stu-id="03553-128">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03553-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03553-129">See Also</span></span>  
 <span data-ttu-id="03553-130">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="03553-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="03553-131">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="03553-131">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

