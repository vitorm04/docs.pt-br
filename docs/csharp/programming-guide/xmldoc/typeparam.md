---
title: '&lt;typeparam&gt; (Guia de Programação em C#)'
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: ec19060008c1c06c54c89dbddee7d24001bcdebc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187108"
---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="33eb5-102">&lt;typeparam&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="33eb5-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="33eb5-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33eb5-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33eb5-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="33eb5-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="33eb5-105">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="33eb5-105">The name of the type parameter.</span></span> <span data-ttu-id="33eb5-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="33eb5-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="33eb5-107">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="33eb5-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33eb5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="33eb5-108">Remarks</span></span>  
 <span data-ttu-id="33eb5-109">A marca `<typeparam>` deve ser usada no comentário para um tipo genérico ou para uma declaração de método descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="33eb5-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="33eb5-110">Adicione uma marca para cada parâmetro de tipo do tipo ou do método genérico.</span><span class="sxs-lookup"><span data-stu-id="33eb5-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="33eb5-111">Para obter mais informações, consulte [Genéricos](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="33eb5-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="33eb5-112">O texto da marca `<typeparam>` será exibido no IntelliSense, o relatório Web de comentários sobre código da [Janela do Pesquisador de Objetos](https://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda).</span><span class="sxs-lookup"><span data-stu-id="33eb5-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](https://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="33eb5-113">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="33eb5-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33eb5-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33eb5-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="33eb5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33eb5-115">See Also</span></span>

- [<span data-ttu-id="33eb5-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="33eb5-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="33eb5-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="33eb5-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="33eb5-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="33eb5-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
