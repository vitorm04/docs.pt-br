---
title: <param> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287318"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="b99d8-102">\<param>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="b99d8-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b99d8-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b99d8-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="b99d8-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b99d8-104">Parameters</span></span>

- `name`

  <span data-ttu-id="b99d8-105">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="b99d8-105">The name of a method parameter.</span></span> <span data-ttu-id="b99d8-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="b99d8-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="b99d8-107">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b99d8-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="b99d8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b99d8-108">Remarks</span></span>

<span data-ttu-id="b99d8-109">A `<param>` marca deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros para o método.</span><span class="sxs-lookup"><span data-stu-id="b99d8-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="b99d8-110">Para documentar vários parâmetros, use várias `<param>` marcas.</span><span class="sxs-lookup"><span data-stu-id="b99d8-110">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="b99d8-111">O texto da `<param>` marca é exibido no IntelliSense, no Pesquisador de objetos e no relatório da Web de comentários de código.</span><span class="sxs-lookup"><span data-stu-id="b99d8-111">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="b99d8-112">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="b99d8-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b99d8-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b99d8-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="b99d8-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b99d8-114">See also</span></span>

- [<span data-ttu-id="b99d8-115">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="b99d8-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b99d8-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="b99d8-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
