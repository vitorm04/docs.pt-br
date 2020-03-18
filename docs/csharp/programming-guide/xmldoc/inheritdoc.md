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
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156942"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="58330-102">\<herdar> (Guia de Programação C#)</span><span class="sxs-lookup"><span data-stu-id="58330-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="58330-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58330-103">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="58330-104">Herdar Doc</span><span class="sxs-lookup"><span data-stu-id="58330-104">InheritDoc</span></span>

<span data-ttu-id="58330-105">Herde comentários XML de classes básicas, interfaces e métodos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="58330-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="58330-106">Isso elimina a cópia e a cola indesejadas de comentários XML duplicados e mantém automaticamente os comentários XML sincronizados.</span><span class="sxs-lookup"><span data-stu-id="58330-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="58330-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="58330-107">Remarks</span></span>  
<span data-ttu-id="58330-108">Adicione seus comentários XML em classes básicas ou interfaces e deixe o InheritDoc copiar os comentários para implementar classes.</span><span class="sxs-lookup"><span data-stu-id="58330-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="58330-109">Adicione seus comentários XML aos seus métodos síncronos e deixe o InheritDoc copiar os comentários para suas versões assíncronas dos mesmos métodos.</span><span class="sxs-lookup"><span data-stu-id="58330-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="58330-110">Se você quiser copiar os comentários de um `cref` membro específico, você pode usar o atributo para especificar o membro.</span><span class="sxs-lookup"><span data-stu-id="58330-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="58330-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="58330-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="58330-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="58330-112">See also</span></span>

- [<span data-ttu-id="58330-113">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="58330-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="58330-114">Tags recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="58330-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
