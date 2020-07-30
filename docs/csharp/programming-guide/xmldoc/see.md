---
title: <see>-Guia de programação C#
description: Saiba mais sobre a <see> marca XML. Essa marca permite especificar um link de dentro do texto, por exemplo, usando um atributo cref.
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
ms.openlocfilehash: 1cc4982d1ebe9d6896404218a6d200b10cc6503f
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381925"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="8c8a3-104">\<see>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="8c8a3-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8c8a3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c8a3-105">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="8c8a3-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c8a3-106">Parameters</span></span>

- <span data-ttu-id="8c8a3-107">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="8c8a3-107">cref = "`member`"</span></span>

  <span data-ttu-id="8c8a3-108">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-108">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="8c8a3-109">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-109">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="8c8a3-110">Coloque *member* entre aspas duplas (“ ”).</span><span class="sxs-lookup"><span data-stu-id="8c8a3-110">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="8c8a3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c8a3-111">Remarks</span></span>

<span data-ttu-id="8c8a3-112">A `<see>` marca permite especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-112">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="8c8a3-113">Use [\<seealso>](./seealso.md) para indicar que o texto deve ser colocado em uma seção ver também.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-113">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="8c8a3-114">Use o [atributo cref](./cref-attribute.md) para criar hyperlinks internos para páginas de documentação para elementos de código.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-114">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="8c8a3-115">Além disso, ``href`` é um atributo válido que funcionará como um hiperlink.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-115">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="8c8a3-116">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="8c8a3-117">O exemplo a seguir mostra uma `<see>` marca em uma seção de resumo.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-117">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="8c8a3-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="8c8a3-118">See also</span></span>

- [<span data-ttu-id="8c8a3-119">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="8c8a3-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8c8a3-120">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="8c8a3-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
