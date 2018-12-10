---
title: '&lt;typeparam&gt; (Guia de Programação em C#)'
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5db257cc655b7d9112fc4efc917f5d2175fcf665
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143110"
---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="ec2a2-102">&lt;typeparam&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ec2a2-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ec2a2-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec2a2-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec2a2-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec2a2-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ec2a2-105">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-105">The name of the type parameter.</span></span> <span data-ttu-id="ec2a2-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="ec2a2-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ec2a2-107">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec2a2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec2a2-108">Remarks</span></span>  
 <span data-ttu-id="ec2a2-109">A marca `<typeparam>` deve ser usada no comentário para um tipo genérico ou para uma declaração de método descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="ec2a2-110">Adicione uma marca para cada parâmetro de tipo do tipo ou do método genérico.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="ec2a2-111">Para obter mais informações, consulte [Genéricos](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="ec2a2-112">O texto da marca `<typeparam>` será exibido no IntelliSense, o relatório Web de comentários sobre código da [Janela do Pesquisador de Objetos](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="ec2a2-113">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec2a2-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec2a2-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ec2a2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec2a2-115">See Also</span></span>

- [<span data-ttu-id="ec2a2-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ec2a2-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ec2a2-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ec2a2-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ec2a2-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="ec2a2-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
