---
title: <include> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: bf41019c775fed25afe4bdb9453a8e52f44856b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287344"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="2694e-102">\<include>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="2694e-102">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2694e-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2694e-103">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="2694e-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2694e-104">Parameters</span></span>

- `filename`

  <span data-ttu-id="2694e-105">O nome do arquivo XML que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="2694e-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="2694e-106">O nome do arquivo pode ser qualificado com um caminho relativo ao arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="2694e-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="2694e-107">Coloque `filename` entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="2694e-107">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="2694e-108">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="2694e-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="2694e-109">Coloque o caminho entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="2694e-109">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="2694e-110">O especificador de nome na marca que precede os comentários; `name` terá um `id`.</span><span class="sxs-lookup"><span data-stu-id="2694e-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="2694e-111">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="2694e-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="2694e-112">Coloque a ID entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="2694e-112">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="2694e-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="2694e-113">Remarks</span></span>

<span data-ttu-id="2694e-114">A `<include>` marca permite que você faça referência a comentários em outro arquivo que descreva os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="2694e-114">The `<include>` tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="2694e-115">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="2694e-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="2694e-116">Colocando a documentação em um arquivo separado, é possível aplicar o controle do código-fonte à documentação separadamente do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="2694e-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="2694e-117">Uma pessoa pode fazer o check-out do arquivo de código-fonte e outra pessoa pode fazer o check-out do arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="2694e-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="2694e-118">A `<include>` marca usa a sintaxe XPath XML.</span><span class="sxs-lookup"><span data-stu-id="2694e-118">The `<include>` tag uses the XML XPath syntax.</span></span> <span data-ttu-id="2694e-119">Consulte a documentação do XPath para obter maneiras de personalizar seu `<include>` uso.</span><span class="sxs-lookup"><span data-stu-id="2694e-119">Refer to XPath documentation for ways to customize your `<include>` use.</span></span>

## <a name="example"></a><span data-ttu-id="2694e-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2694e-120">Example</span></span>

<span data-ttu-id="2694e-121">Este é um exemplo de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="2694e-121">This is a multifile example.</span></span> <span data-ttu-id="2694e-122">Este é o primeiro arquivo, que usa `<include>` .</span><span class="sxs-lookup"><span data-stu-id="2694e-122">The following is the first file, which uses `<include>`.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="2694e-123">O segundo arquivo, *xml_include_tag. doc*, contém os comentários de documentação a seguir.</span><span class="sxs-lookup"><span data-stu-id="2694e-123">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

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

## <a name="program-output"></a><span data-ttu-id="2694e-124">Saída do programa</span><span class="sxs-lookup"><span data-stu-id="2694e-124">Program output</span></span>

<span data-ttu-id="2694e-125">A seguinte saída é gerada quando você compila as classes Test e Test2 com a seguinte linha de comando: `-doc:DocFileName.xml.` No Visual Studio, especifique a opção de comentários de documentos XML no painel Compilar do Designer de Projeto.</span><span class="sxs-lookup"><span data-stu-id="2694e-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="2694e-126">Quando o compilador C# vê a `<include>` marca, ele pesquisa comentários de documentação em *xml_include_tag. doc* em vez do arquivo de origem atual.</span><span class="sxs-lookup"><span data-stu-id="2694e-126">When the C# compiler sees the `<include>` tag, it searches for documentation comments in *xml_include_tag.doc* instead of the current source file.</span></span> <span data-ttu-id="2694e-127">O compilador, em seguida, gera o *testcfilename. xml*, e esse é o arquivo que é consumido por ferramentas de documentação como [DocFX](https://dotnet.github.io/docfx/) e [Sandcastle](https://github.com/EWSoftware/SHFB) para produzir a documentação final.</span><span class="sxs-lookup"><span data-stu-id="2694e-127">The compiler then generates *DocFileName.xml*, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2694e-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="2694e-128">See also</span></span>

- [<span data-ttu-id="2694e-129">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="2694e-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2694e-130">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="2694e-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
