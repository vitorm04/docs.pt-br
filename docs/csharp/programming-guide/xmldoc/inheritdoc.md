---
title: <inheritdoc> – Guia de Programação em C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d660cb1739733c4e98ae0b7939476fe74e6cf200
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795157"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="8f85e-102">\<inheritdoc > (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="8f85e-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f85e-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f85e-103">Syntax</span></span>  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a><span data-ttu-id="8f85e-104">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="8f85e-104">InheritDoc</span></span>

<span data-ttu-id="8f85e-105">Herde comentários XML de classes base, interfaces e métodos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="8f85e-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="8f85e-106">Isso elimina a cópia indesejada e a colagem de comentários XML duplicados e mantém automaticamente os comentários XML sincronizados.</span><span class="sxs-lookup"><span data-stu-id="8f85e-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="8f85e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f85e-107">Remarks</span></span>  
<span data-ttu-id="8f85e-108">Adicione seus comentários XML em classes ou interfaces base e deixe que InheritDoc Copie os comentários para a implementação de classes.</span><span class="sxs-lookup"><span data-stu-id="8f85e-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="8f85e-109">Adicione seus comentários XML aos seus métodos síncronos e deixe que InheritDoc Copie os comentários para suas versões assíncronas dos mesmos métodos.</span><span class="sxs-lookup"><span data-stu-id="8f85e-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="8f85e-110">Se você quiser copiar os comentários de um membro específico, poderá usar o atributo `cref` para especificar o membro.</span><span class="sxs-lookup"><span data-stu-id="8f85e-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="8f85e-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8f85e-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="8f85e-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="8f85e-112">See also</span></span>

- [<span data-ttu-id="8f85e-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8f85e-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8f85e-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="8f85e-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
