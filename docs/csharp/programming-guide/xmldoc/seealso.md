---
title: <seealso> -Guia de programação C#
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
ms.openlocfilehash: 1b801ac1b5a0a59d97ccc35ec78930d99223e846
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287214"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="012f7-102">\<seealso>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="012f7-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="012f7-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="012f7-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="012f7-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="012f7-104">Parameters</span></span>

- <span data-ttu-id="012f7-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="012f7-105">cref = " `member`"</span></span>

  <span data-ttu-id="012f7-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="012f7-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="012f7-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.`member`</span><span class="sxs-lookup"><span data-stu-id="012f7-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="012f7-108">deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="012f7-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="012f7-109">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [atributo cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="012f7-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="012f7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="012f7-110">Remarks</span></span>

<span data-ttu-id="012f7-111">A `<seealso>` marca permite especificar o texto que você pode querer que apareça em uma seção ver também.</span><span class="sxs-lookup"><span data-stu-id="012f7-111">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="012f7-112">Use [\<see>](./see.md) para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="012f7-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="012f7-113">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="012f7-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="012f7-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="012f7-114">Example</span></span>

<span data-ttu-id="012f7-115">Consulte [\<summary>](./summary.md) para obter um exemplo de como usar \<seealso> .</span><span class="sxs-lookup"><span data-stu-id="012f7-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="012f7-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="012f7-116">See also</span></span>

- [<span data-ttu-id="012f7-117">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="012f7-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="012f7-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="012f7-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
