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
ms.openlocfilehash: 4d967d671b3a27698b457c80ff5a8f7031dc6bcb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587417"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="d621e-102">\<value> (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d621e-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d621e-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d621e-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d621e-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d621e-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="d621e-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d621e-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d621e-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d621e-106">Remarks</span></span>  
 <span data-ttu-id="d621e-107">A marca \<value> permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="d621e-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="d621e-108">Observe que quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento do Visual Studio .NET, ele adicionará uma marca [\<summary>](./summary.md) para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="d621e-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="d621e-109">Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="d621e-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="d621e-110">Compile com [/doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d621e-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d621e-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d621e-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="d621e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d621e-112">See also</span></span>

- [<span data-ttu-id="d621e-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d621e-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d621e-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="d621e-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
