---
title: Comentários de documentação XML (Guia de Programação em C#)
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
ms.openlocfilehash: 2f3bc5780e202bc5905cc027821f937b75335454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359164"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="bbb85-102">Comentários de documentação XML (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="bbb85-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="bbb85-103">No Visual C#, você pode criar documentação para seu código ao incluir elementos XML nos campos de comentários especiais (indicados por barras triplas) no código-fonte logo antes do bloco de código ao qual os comentários se referem, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bbb85-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 <span data-ttu-id="bbb85-104">Ao compilar com a opção [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md), o compilador pesquisará todas as marcas XML no código-fonte e criará um arquivo de documentação XML.</span><span class="sxs-lookup"><span data-stu-id="bbb85-104">When you compile with the [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="bbb85-105">Para criar a documentação final com base no arquivo gerado pelo compilador, você pode criar uma ferramenta personalizada ou usar uma ferramenta como a [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="bbb85-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="bbb85-106">Para consultar elementos XML (por exemplo, sua função processa elementos XML específicos que você deseja descrever em um comentário da documentação XML), você pode usar o mecanismo de citação padrão (`<` e `>`).</span><span class="sxs-lookup"><span data-stu-id="bbb85-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="bbb85-107">Para consultar identificadores genéricos em elementos de referência de código (`cref`), você pode usar os caracteres de escape (por exemplo, `cref="List&lt;T&gt;"`) ou chaves (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="bbb85-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="bbb85-108">Como um caso especial, o compilador analisa as chaves como colchetes angulares para tornar o comentário da documentação menos incômodo para o autor ao fazer referência a identificadores genéricos.</span><span class="sxs-lookup"><span data-stu-id="bbb85-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbb85-109">Os comentários da documentação XML não são metadados; eles não estão incluídos no assembly compilado e, portanto, não são acessíveis através de reflexão.</span><span class="sxs-lookup"><span data-stu-id="bbb85-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bbb85-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bbb85-110">In This Section</span></span>  
  
-   [<span data-ttu-id="bbb85-111">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="bbb85-111">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="bbb85-112">Processando o Arquivo XML</span><span class="sxs-lookup"><span data-stu-id="bbb85-112">Processing the XML File</span></span>](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="bbb85-113">Delimitadores para marcas de documentação</span><span class="sxs-lookup"><span data-stu-id="bbb85-113">Delimiters for Documentation Tags</span></span>](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [<span data-ttu-id="bbb85-114">Como usar os recursos da documentação XML</span><span class="sxs-lookup"><span data-stu-id="bbb85-114">How to: Use the XML Documentation Features</span></span>](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="bbb85-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="bbb85-115">Related Sections</span></span>  
 <span data-ttu-id="bbb85-116">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="bbb85-116">For more information, see:</span></span>  
  
-   [<span data-ttu-id="bbb85-117">/doc (comentários da documentação de processos)</span><span class="sxs-lookup"><span data-stu-id="bbb85-117">/doc (Process Documentation Comments)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="bbb85-118">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="bbb85-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbb85-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbb85-119">See Also</span></span>  
 [<span data-ttu-id="bbb85-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bbb85-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
