---
title: <seealso> - C# guia de programação
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
ms.openlocfilehash: ad22b423d085a152f47c4e34d7ee4247ef9836b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789688"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="18849-102">\<seeAlso > (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="18849-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="18849-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18849-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="18849-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18849-104">Parameters</span></span>

- <span data-ttu-id="18849-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="18849-105">cref = " `member`"</span></span>

  <span data-ttu-id="18849-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="18849-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="18849-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.`member`</span><span class="sxs-lookup"><span data-stu-id="18849-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="18849-108">deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="18849-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="18849-109">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [\<consulte>](./see.md).</span><span class="sxs-lookup"><span data-stu-id="18849-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="18849-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="18849-110">Remarks</span></span>

<span data-ttu-id="18849-111">A marca \<seealso > permite especificar o texto que você quer que seja exibido na seção Ver também.</span><span class="sxs-lookup"><span data-stu-id="18849-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="18849-112">Use [\<see>](./see.md) para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="18849-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="18849-113">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="18849-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="18849-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18849-114">Example</span></span>

<span data-ttu-id="18849-115">Consulte [\<summary>](./summary.md) para obter um exemplo sobre o uso de \<seealso>.</span><span class="sxs-lookup"><span data-stu-id="18849-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="18849-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="18849-116">See also</span></span>

- [<span data-ttu-id="18849-117">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="18849-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="18849-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="18849-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
