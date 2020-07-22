---
title: <see>-Guia de programação C#
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
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863780"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="83b26-102">\<see>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="83b26-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="83b26-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83b26-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="83b26-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83b26-104">Parameters</span></span>

- <span data-ttu-id="83b26-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="83b26-105">cref = "`member`"</span></span>

  <span data-ttu-id="83b26-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="83b26-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="83b26-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="83b26-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="83b26-108">Coloque *member* entre aspas duplas (“ ”).</span><span class="sxs-lookup"><span data-stu-id="83b26-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="83b26-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="83b26-109">Remarks</span></span>

<span data-ttu-id="83b26-110">A `<see>` marca permite especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="83b26-110">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="83b26-111">Use [\<seealso>](./seealso.md) para indicar que o texto deve ser colocado em uma seção ver também.</span><span class="sxs-lookup"><span data-stu-id="83b26-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="83b26-112">Use o [atributo cref](./cref-attribute.md) para criar hyperlinks internos para páginas de documentação para elementos de código.</span><span class="sxs-lookup"><span data-stu-id="83b26-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="83b26-113">Além disso, ``href`` é um atributo válido que funcionará como um hiperlink.</span><span class="sxs-lookup"><span data-stu-id="83b26-113">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="83b26-114">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="83b26-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="83b26-115">O exemplo a seguir mostra uma `<see>` marca em uma seção de resumo.</span><span class="sxs-lookup"><span data-stu-id="83b26-115">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="83b26-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="83b26-116">See also</span></span>

- [<span data-ttu-id="83b26-117">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="83b26-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="83b26-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="83b26-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
