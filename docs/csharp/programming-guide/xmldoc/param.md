---
title: <param> - Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789766"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="51b05-102">\<param> (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="51b05-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="51b05-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51b05-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="51b05-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="51b05-104">Parameters</span></span>

- `name`

  <span data-ttu-id="51b05-105">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="51b05-105">The name of a method parameter.</span></span> <span data-ttu-id="51b05-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="51b05-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="51b05-107">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="51b05-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="51b05-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="51b05-108">Remarks</span></span>

<span data-ttu-id="51b05-109">A marca \<param> deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="51b05-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="51b05-110">Para documentar vários parâmetros, use várias marcas \<param>.</span><span class="sxs-lookup"><span data-stu-id="51b05-110">To document multiple parameters, use multiple \<param> tags.</span></span>

<span data-ttu-id="51b05-111">O texto da marca \<param> será exibido no IntelliSense, o Pesquisador de Objetos e no relatório Web de comentários sobre código.</span><span class="sxs-lookup"><span data-stu-id="51b05-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>

<span data-ttu-id="51b05-112">Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="51b05-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="51b05-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51b05-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="51b05-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="51b05-114">See also</span></span>

- [<span data-ttu-id="51b05-115">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="51b05-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="51b05-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="51b05-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
