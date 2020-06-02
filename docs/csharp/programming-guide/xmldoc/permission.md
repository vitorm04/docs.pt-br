---
title: <permission> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: bb7172042f0b472d03c3fa2d9dbd0d4d4265076b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287266"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="0cd7d-102">\<permission>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="0cd7d-102">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="0cd7d-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cd7d-103">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="0cd7d-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0cd7d-104">Parameters</span></span>

- <span data-ttu-id="0cd7d-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="0cd7d-105">cref = " `member`"</span></span>

  <span data-ttu-id="0cd7d-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="0cd7d-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="0cd7d-107">O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="0cd7d-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="0cd7d-108">*member* deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="0cd7d-108">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="0cd7d-109">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [atributo cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="0cd7d-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="0cd7d-110">Uma descrição do acesso ao membro.</span><span class="sxs-lookup"><span data-stu-id="0cd7d-110">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cd7d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0cd7d-111">Remarks</span></span>

<span data-ttu-id="0cd7d-112">A `<permission>` marca permite documentar o acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="0cd7d-112">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="0cd7d-113">A classe <xref:System.Security.PermissionSet> permite que você especifique o acesso a um membro.</span><span class="sxs-lookup"><span data-stu-id="0cd7d-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="0cd7d-114">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="0cd7d-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="0cd7d-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0cd7d-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="0cd7d-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="0cd7d-116">See also</span></span>

- [<span data-ttu-id="0cd7d-117">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="0cd7d-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="0cd7d-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="0cd7d-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
