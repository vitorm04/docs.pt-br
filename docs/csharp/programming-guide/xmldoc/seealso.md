---
title: <seealso> -Guia de programação C#
description: Saiba como usar o XML <seealso> Tags. Essa marca permite especificar o texto que você pode querer que apareça em uma seção ' Ver também '.
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e8618ef352a4fa7f0fd4c88733c6568b0e12e376
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380638"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="83721-105">\<seealso>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="83721-105">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="83721-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83721-106">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="83721-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="83721-107">Parameters</span></span>

- <span data-ttu-id="83721-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="83721-108">cref = " `member`"</span></span>

  <span data-ttu-id="83721-109">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="83721-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="83721-110">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.`member`</span><span class="sxs-lookup"><span data-stu-id="83721-110">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="83721-111">deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="83721-111">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="83721-112">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [atributo cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="83721-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="83721-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="83721-113">Remarks</span></span>

<span data-ttu-id="83721-114">A `<seealso>` marca permite especificar o texto que você pode querer que apareça em uma seção ver também.</span><span class="sxs-lookup"><span data-stu-id="83721-114">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="83721-115">Use [\<see>](./see.md) para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="83721-115">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="83721-116">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="83721-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="83721-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83721-117">Example</span></span>

<span data-ttu-id="83721-118">Consulte [\<summary>](./summary.md) para obter um exemplo de como usar \<seealso> .</span><span class="sxs-lookup"><span data-stu-id="83721-118">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="83721-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="83721-119">See also</span></span>

- [<span data-ttu-id="83721-120">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="83721-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="83721-121">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="83721-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
