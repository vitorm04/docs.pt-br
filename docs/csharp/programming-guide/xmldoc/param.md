---
title: <param> -Guia de programação C#
description: Saiba mais sobre o XML <param> Tags. Essa marca é usada no comentário para uma declaração de método para descrever um dos parâmetros para o método.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381548"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="1ecdb-105">\<param>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="1ecdb-105">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ecdb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ecdb-106">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="1ecdb-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ecdb-107">Parameters</span></span>

- `name`

  <span data-ttu-id="1ecdb-108">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-108">The name of a method parameter.</span></span> <span data-ttu-id="1ecdb-109">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="1ecdb-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="1ecdb-110">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-110">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ecdb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ecdb-111">Remarks</span></span>

<span data-ttu-id="1ecdb-112">A `<param>` marca deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros para o método.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-112">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="1ecdb-113">Para documentar vários parâmetros, use várias `<param>` marcas.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-113">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="1ecdb-114">O texto da `<param>` marca é exibido no IntelliSense, no Pesquisador de objetos e no relatório da Web de comentários de código.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-114">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="1ecdb-115">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-115">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1ecdb-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ecdb-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="1ecdb-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ecdb-117">See also</span></span>

- [<span data-ttu-id="1ecdb-118">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="1ecdb-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1ecdb-119">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="1ecdb-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
