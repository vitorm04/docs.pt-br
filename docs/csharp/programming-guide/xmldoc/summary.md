---
title: <summary> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789669"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="a46cd-102">> de Resumo deC# \<(guia de programação)</span><span class="sxs-lookup"><span data-stu-id="a46cd-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a46cd-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a46cd-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="a46cd-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a46cd-104">Parameters</span></span>

- `description`

  <span data-ttu-id="a46cd-105">Um resumo do objeto.</span><span class="sxs-lookup"><span data-stu-id="a46cd-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="a46cd-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a46cd-106">Remarks</span></span>

<span data-ttu-id="a46cd-107">A marca \<summary> deve ser usada para descrever um tipo ou um membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="a46cd-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="a46cd-108">Use [\<remarks>](./remarks.md) para adicionar mais informações a uma descrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="a46cd-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="a46cd-109">Use o [atributo cref](./cref-attribute.md) para habilitar ferramentas de documentação como o [DocFX](https://dotnet.github.io/docfx/) e o [Sandcastle](https://github.com/EWSoftware/SHFB) para criar hiperlinks internos para páginas de documentação em elementos de código.</span><span class="sxs-lookup"><span data-stu-id="a46cd-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="a46cd-110">O texto da marca \<summary> é a única fonte de informações sobre o tipo no IntelliSense e também é exibido na janela Pesquisador de Objetos.</span><span class="sxs-lookup"><span data-stu-id="a46cd-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="a46cd-111">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a46cd-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="a46cd-112">Para criar a documentação final com base no arquivo gerado pelo compilador, crie uma ferramenta personalizada ou use uma ferramenta como o [DocFX](https://dotnet.github.io/docfx/) ou o [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="a46cd-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="a46cd-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a46cd-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="a46cd-114">O exemplo anterior produz o seguinte arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="a46cd-114">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            <seealso cref="M:TestClass.Main"/>
            </summary>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="a46cd-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a46cd-115">Example</span></span>

<span data-ttu-id="a46cd-116">O exemplo a seguir mostra como fazer uma referência `cref` para um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="a46cd-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="a46cd-117">O exemplo anterior produz o seguinte arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="a46cd-117">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="a46cd-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="a46cd-118">See also</span></span>

- [<span data-ttu-id="a46cd-119">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="a46cd-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a46cd-120">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="a46cd-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
