---
title: <summary> - Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789669"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="ec1f3-102">\<resumo> (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="ec1f3-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec1f3-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec1f3-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="ec1f3-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec1f3-104">Parameters</span></span>

- `description`

  <span data-ttu-id="ec1f3-105">Um resumo do objeto.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec1f3-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec1f3-106">Remarks</span></span>

<span data-ttu-id="ec1f3-107">A marca \<summary> deve ser usada para descrever um tipo ou um membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="ec1f3-108">Use [ \<observações>](./remarks.md) para adicionar informações suplementares a uma descrição do tipo.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="ec1f3-109">Use o [atributo cref](./cref-attribute.md) para habilitar ferramentas de documentação como o [DocFX](https://dotnet.github.io/docfx/) e o [Sandcastle](https://github.com/EWSoftware/SHFB) para criar hiperlinks internos para páginas de documentação em elementos de código.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="ec1f3-110">O texto da marca \<summary> é a única fonte de informações sobre o tipo no IntelliSense e também é exibido na janela Pesquisador de Objetos.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="ec1f3-111">Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="ec1f3-112">Para criar a documentação final com base no arquivo gerado pelo compilador, você pode criar uma ferramenta personalizada ou usar uma ferramenta como [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="ec1f3-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="ec1f3-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec1f3-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="ec1f3-114">O exemplo anterior produz o seguinte arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-114">The previous example produces the following XML file.</span></span>

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

## <a name="example"></a><span data-ttu-id="ec1f3-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec1f3-115">Example</span></span>

<span data-ttu-id="ec1f3-116">O exemplo a seguir mostra como fazer uma referência `cref` para um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="ec1f3-117">O exemplo anterior produz o seguinte arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="ec1f3-117">The previous example produces the following XML file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec1f3-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec1f3-118">See also</span></span>

- [<span data-ttu-id="ec1f3-119">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="ec1f3-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="ec1f3-120">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="ec1f3-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
