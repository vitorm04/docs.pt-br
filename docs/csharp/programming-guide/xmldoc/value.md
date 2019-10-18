---
title: <value> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 09577d931c6b1f571cd4112c788da38bab85bf42
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523270"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="5dd06-102">\<value> (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5dd06-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="5dd06-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dd06-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dd06-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5dd06-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="5dd06-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="5dd06-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dd06-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="5dd06-106">Remarks</span></span>  
 <span data-ttu-id="5dd06-107">A marca \<value> permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="5dd06-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="5dd06-108">Observe que quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento do Visual Studio .NET, ele adicionará uma marca [\<summary>](./summary.md) para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="5dd06-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="5dd06-109">Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="5dd06-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="5dd06-110">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="5dd06-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dd06-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5dd06-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="5dd06-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dd06-112">See also</span></span>

- [<span data-ttu-id="5dd06-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5dd06-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5dd06-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="5dd06-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
