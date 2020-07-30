---
title: <include> -Guia de programação C#
description: Saiba mais sobre o XML <include> Tags. Essa marca permite que você faça referência a comentários em outro arquivo que descreva os tipos e membros em seu código-fonte.
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 15a99444d464594cc91a7c8805c564c703c3b608
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381899"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="776ba-105">\<include>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="776ba-105">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="776ba-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="776ba-106">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="776ba-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="776ba-107">Parameters</span></span>

- `filename`

  <span data-ttu-id="776ba-108">O nome do arquivo XML que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="776ba-108">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="776ba-109">O nome do arquivo pode ser qualificado com um caminho relativo ao arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="776ba-109">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="776ba-110">Coloque `filename` entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="776ba-110">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="776ba-111">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="776ba-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="776ba-112">Coloque o caminho entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="776ba-112">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="776ba-113">O especificador de nome na marca que precede os comentários; `name` terá um `id`.</span><span class="sxs-lookup"><span data-stu-id="776ba-113">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="776ba-114">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="776ba-114">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="776ba-115">Coloque a ID entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="776ba-115">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="776ba-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="776ba-116">Remarks</span></span>

<span data-ttu-id="776ba-117">A `<include>` marca permite que você faça referência a comentários em outro arquivo que descreva os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="776ba-117">The `<include>` tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="776ba-118">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="776ba-118">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="776ba-119">Colocando a documentação em um arquivo separado, é possível aplicar o controle do código-fonte à documentação separadamente do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="776ba-119">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="776ba-120">Uma pessoa pode fazer o check-out do arquivo de código-fonte e outra pessoa pode fazer o check-out do arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="776ba-120">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="776ba-121">A `<include>` marca usa a sintaxe XPath XML.</span><span class="sxs-lookup"><span data-stu-id="776ba-121">The `<include>` tag uses the XML XPath syntax.</span></span> <span data-ttu-id="776ba-122">Consulte a documentação do XPath para obter maneiras de personalizar seu `<include>` uso.</span><span class="sxs-lookup"><span data-stu-id="776ba-122">Refer to XPath documentation for ways to customize your `<include>` use.</span></span>

## <a name="example"></a><span data-ttu-id="776ba-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="776ba-123">Example</span></span>

<span data-ttu-id="776ba-124">Este é um exemplo de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="776ba-124">This is a multifile example.</span></span> <span data-ttu-id="776ba-125">Este é o primeiro arquivo, que usa `<include>` .</span><span class="sxs-lookup"><span data-stu-id="776ba-125">The following is the first file, which uses `<include>`.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="776ba-126">O segundo arquivo, *xml_include_tag.doc*, contém os comentários de documentação a seguir.</span><span class="sxs-lookup"><span data-stu-id="776ba-126">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

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

## <a name="program-output"></a><span data-ttu-id="776ba-127">Saída do programa</span><span class="sxs-lookup"><span data-stu-id="776ba-127">Program output</span></span>

<span data-ttu-id="776ba-128">A seguinte saída é gerada quando você compila as classes Test e Test2 com a seguinte linha de comando: `-doc:DocFileName.xml.` No Visual Studio, especifique a opção de comentários de documentos XML no painel Compilar do Designer de Projeto.</span><span class="sxs-lookup"><span data-stu-id="776ba-128">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="776ba-129">Quando o compilador C# vê a `<include>` marca, ele pesquisa comentários de documentação em *xml_include_tag.doc* em vez do arquivo de origem atual.</span><span class="sxs-lookup"><span data-stu-id="776ba-129">When the C# compiler sees the `<include>` tag, it searches for documentation comments in *xml_include_tag.doc* instead of the current source file.</span></span> <span data-ttu-id="776ba-130">Em seguida, o compilador gera *DocFileName.xml*, e esse é o arquivo que é consumido por ferramentas de documentação, como o [Sandcastle](https://github.com/EWSoftware/SHFB) , para produzir a documentação final.</span><span class="sxs-lookup"><span data-stu-id="776ba-130">The compiler then generates *DocFileName.xml*, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="776ba-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="776ba-131">See also</span></span>

- [<span data-ttu-id="776ba-132">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="776ba-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="776ba-133">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="776ba-133">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
