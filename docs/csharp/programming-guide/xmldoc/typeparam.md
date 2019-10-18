---
title: <typeparam> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: e5e0d7be46e02bd30799b54246db729ae63ca300
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523290"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="d3678-102">\<typeparam> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d3678-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d3678-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3678-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3678-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d3678-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d3678-105">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="d3678-105">The name of the type parameter.</span></span> <span data-ttu-id="d3678-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="d3678-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d3678-107">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="d3678-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3678-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3678-108">Remarks</span></span>  
 <span data-ttu-id="d3678-109">A marca `<typeparam>` deve ser usada no comentário para um tipo genérico ou para uma declaração de método descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="d3678-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="d3678-110">Adicione uma marca para cada parâmetro de tipo do tipo ou do método genérico.</span><span class="sxs-lookup"><span data-stu-id="d3678-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="d3678-111">Para obter mais informações, consulte [Genéricos](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3678-111">For more information, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="d3678-112">O texto da marca `<typeparam>` será exibido no IntelliSense, o relatório Web de comentários sobre código da [Janela do Pesquisador de Objetos](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser).</span><span class="sxs-lookup"><span data-stu-id="d3678-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="d3678-113">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d3678-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3678-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3678-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="d3678-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3678-115">See also</span></span>

- [<span data-ttu-id="d3678-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d3678-116">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="d3678-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d3678-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d3678-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="d3678-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
