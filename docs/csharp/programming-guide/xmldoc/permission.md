---
title: <permission> -Guia de programação C#
description: Saiba mais sobre o XML <permission> Tags. Essa marca permite documentar o acesso de um membro, enquanto a classe PermissionSet permite que você especifique o acesso a um membro.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381717"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="e496a-105">\<permission>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="e496a-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e496a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e496a-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="e496a-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e496a-107">Parameters</span></span>

- <span data-ttu-id="e496a-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="e496a-108">cref = " `member`"</span></span>

  <span data-ttu-id="e496a-109">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="e496a-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="e496a-110">O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="e496a-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="e496a-111">*member* deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="e496a-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="e496a-112">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [atributo cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="e496a-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="e496a-113">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="e496a-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="e496a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="e496a-114">Remarks</span></span>

<span data-ttu-id="e496a-115">A `<permission>` marca permite documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="e496a-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="e496a-116">A classe <xref:System.Security.PermissionSet> permite que você especifique o acesso a um membro.</span><span class="sxs-lookup"><span data-stu-id="e496a-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="e496a-117">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e496a-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="e496a-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e496a-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="e496a-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="e496a-119">See also</span></span>

- [<span data-ttu-id="e496a-120">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="e496a-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e496a-121">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="e496a-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
