---
title: Guia de C# programação de <see>
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 17d1d344b9a27ffd4995fa4849ee6d5ce7f90f29
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789696"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="89b43-102">\<consulte > (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="89b43-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="89b43-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89b43-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="89b43-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89b43-104">Parameters</span></span>

- <span data-ttu-id="89b43-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="89b43-105">cref = " `member`"</span></span>

  <span data-ttu-id="89b43-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="89b43-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="89b43-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="89b43-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="89b43-108">Coloque *member* entre aspas duplas (“ ”).</span><span class="sxs-lookup"><span data-stu-id="89b43-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="89b43-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="89b43-109">Remarks</span></span>

<span data-ttu-id="89b43-110">Use a marca \<see> para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="89b43-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="89b43-111">Use [\<seealso>](./seealso.md) para indicar que o texto deve ser colocado em uma seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="89b43-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="89b43-112">Use o [atributo cref](./cref-attribute.md) para criar hyperlinks internos para páginas de documentação para elementos de código.</span><span class="sxs-lookup"><span data-stu-id="89b43-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="89b43-113">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="89b43-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="89b43-114">O exemplo a seguir mostra uma marca \<see> dentro de uma seção de resumo.</span><span class="sxs-lookup"><span data-stu-id="89b43-114">The following example shows a \<see> tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="89b43-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="89b43-115">See also</span></span>

- [<span data-ttu-id="89b43-116">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="89b43-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="89b43-117">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="89b43-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
