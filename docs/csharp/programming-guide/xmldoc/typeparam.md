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
ms.openlocfilehash: 9150ab3e29eaa6b692e2ab2be90bb0e87ba54941
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978638"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="8eb15-102">\<typeparam> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8eb15-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="8eb15-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8eb15-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8eb15-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8eb15-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8eb15-105">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="8eb15-105">The name of the type parameter.</span></span> <span data-ttu-id="8eb15-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="8eb15-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="8eb15-107">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="8eb15-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eb15-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8eb15-108">Remarks</span></span>  
 <span data-ttu-id="8eb15-109">A marca `<typeparam>` deve ser usada no comentário para um tipo genérico ou para uma declaração de método descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="8eb15-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="8eb15-110">Adicione uma marca para cada parâmetro de tipo do tipo ou do método genérico.</span><span class="sxs-lookup"><span data-stu-id="8eb15-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="8eb15-111">Para obter mais informações, consulte [Genéricos](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="8eb15-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="8eb15-112">O texto da marca `<typeparam>` será exibido no IntelliSense, o relatório Web de comentários sobre código da [Janela do Pesquisador de Objetos](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser).</span><span class="sxs-lookup"><span data-stu-id="8eb15-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="8eb15-113">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="8eb15-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eb15-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8eb15-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="8eb15-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8eb15-115">See also</span></span>

- [<span data-ttu-id="8eb15-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8eb15-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="8eb15-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8eb15-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8eb15-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="8eb15-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
