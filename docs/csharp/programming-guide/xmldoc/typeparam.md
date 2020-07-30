---
title: <typeparam> -Guia de programação C#
description: Saiba mais sobre o XML <typeparam> Tags. Essa marca é usada no comentário para um tipo genérico ou declaração de método para descrever um parâmetro de tipo.
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380781"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="9019a-105">\<typeparam>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="9019a-105">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9019a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9019a-106">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="9019a-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9019a-107">Parameters</span></span>

- `name`

  <span data-ttu-id="9019a-108">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9019a-108">The name of the type parameter.</span></span> <span data-ttu-id="9019a-109">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="9019a-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="9019a-110">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9019a-110">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="9019a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9019a-111">Remarks</span></span>

<span data-ttu-id="9019a-112">A marca `<typeparam>` deve ser usada no comentário para um tipo genérico ou para uma declaração de método descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="9019a-112">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="9019a-113">Adicione uma marca para cada parâmetro de tipo do tipo ou do método genérico.</span><span class="sxs-lookup"><span data-stu-id="9019a-113">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="9019a-114">Para obter mais informações, consulte [Genéricos](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="9019a-114">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="9019a-115">O texto da marca `<typeparam>` será exibido no IntelliSense, o relatório Web de comentários sobre código da [Janela do Pesquisador de Objetos](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser).</span><span class="sxs-lookup"><span data-stu-id="9019a-115">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="9019a-116">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="9019a-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="9019a-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9019a-117">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="9019a-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="9019a-118">See also</span></span>

- [<span data-ttu-id="9019a-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9019a-119">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9019a-120">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="9019a-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="9019a-121">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="9019a-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
