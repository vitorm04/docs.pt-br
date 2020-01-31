---
title: Comentários de documentação XML C# -guia de programação
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: f5a507bc35b0cc0a679fd055bfc255bb3cb9a090
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789791"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="954cb-102">Comentários de documentação XMLC# (guia de programação)</span><span class="sxs-lookup"><span data-stu-id="954cb-102">XML documentation comments (C# programming guide)</span></span>

<span data-ttu-id="954cb-103">No C#, você pode criar documentação para seu código, incluindo elementos XML em campos de comentário especiais (indicados por barras triplas) no código-fonte diretamente antes do bloco de código ao qual os comentários se referem, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="954cb-103">In C#, you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example.</span></span>

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

<span data-ttu-id="954cb-104">Quando você compilar com a opção [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) , o compilador pesquisará todas as marcas XML no código-fonte e criará um arquivo de documentação XML.</span><span class="sxs-lookup"><span data-stu-id="954cb-104">When you compile with the [-doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="954cb-105">Para criar a documentação final com base no arquivo gerado pelo compilador, crie uma ferramenta personalizada ou use uma ferramenta como o [DocFX](https://dotnet.github.io/docfx/) ou o [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="954cb-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="954cb-106">Para consultar elementos XML (por exemplo, sua função processa elementos XML específicos que você deseja descrever em um comentário da documentação XML), você pode usar o mecanismo de citação padrão (`<` e `>`).</span><span class="sxs-lookup"><span data-stu-id="954cb-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="954cb-107">Para consultar identificadores genéricos em elementos de referência de código (`cref`), você pode usar os caracteres de escape (por exemplo, `cref="List&lt;T&gt;"`) ou chaves (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="954cb-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="954cb-108">Como um caso especial, o compilador analisa as chaves como colchetes angulares para tornar o comentário da documentação menos incômodo para o autor ao fazer referência a identificadores genéricos.</span><span class="sxs-lookup"><span data-stu-id="954cb-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>

> [!NOTE]
> <span data-ttu-id="954cb-109">Os comentários da documentação XML não são metadados; eles não estão incluídos no assembly compilado e, portanto, não são acessíveis através de reflexão.</span><span class="sxs-lookup"><span data-stu-id="954cb-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="954cb-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="954cb-110">In this section</span></span>

- [<span data-ttu-id="954cb-111">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="954cb-111">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

- [<span data-ttu-id="954cb-112">Processando o arquivo XML</span><span class="sxs-lookup"><span data-stu-id="954cb-112">Processing the XML file</span></span>](./processing-the-xml-file.md)

- [<span data-ttu-id="954cb-113">Delimitadores para marcas de documentação</span><span class="sxs-lookup"><span data-stu-id="954cb-113">Delimiters for documentation tags</span></span>](./delimiters-for-documentation-tags.md)

- [<span data-ttu-id="954cb-114">Como usar os recursos de documentação XML</span><span class="sxs-lookup"><span data-stu-id="954cb-114">How to use the XML documentation features</span></span>](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a><span data-ttu-id="954cb-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="954cb-115">Related sections</span></span>

<span data-ttu-id="954cb-116">Para obter mais informações, consulte .</span><span class="sxs-lookup"><span data-stu-id="954cb-116">For more information, see:</span></span>

- [<span data-ttu-id="954cb-117">-Doc (comentários de documentação do processo)</span><span class="sxs-lookup"><span data-stu-id="954cb-117">-doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a><span data-ttu-id="954cb-118">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="954cb-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="954cb-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="954cb-119">See also</span></span>

- [<span data-ttu-id="954cb-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="954cb-120">C# Programming Guide</span></span>](../index.md)
