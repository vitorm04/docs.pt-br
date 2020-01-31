---
title: <param> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789766"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="16ead-102">> de \<paramC# (guia de programação)</span><span class="sxs-lookup"><span data-stu-id="16ead-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="16ead-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16ead-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="16ead-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16ead-104">Parameters</span></span>

- `name`

  <span data-ttu-id="16ead-105">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="16ead-105">The name of a method parameter.</span></span> <span data-ttu-id="16ead-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="16ead-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="16ead-107">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="16ead-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="16ead-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="16ead-108">Remarks</span></span>

<span data-ttu-id="16ead-109">A marca \<param> deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="16ead-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="16ead-110">Para documentar vários parâmetros, use várias marcas \<param>.</span><span class="sxs-lookup"><span data-stu-id="16ead-110">To document multiple parameters, use multiple \<param> tags.</span></span>

<span data-ttu-id="16ead-111">O texto da marca \<param> será exibido no IntelliSense, o Pesquisador de Objetos e no relatório Web de comentários sobre código.</span><span class="sxs-lookup"><span data-stu-id="16ead-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>

<span data-ttu-id="16ead-112">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="16ead-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="16ead-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16ead-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="16ead-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="16ead-114">See also</span></span>

- [<span data-ttu-id="16ead-115">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="16ead-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="16ead-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="16ead-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
