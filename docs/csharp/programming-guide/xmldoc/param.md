---
title: '&lt;param&gt; – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: fb31e1d4c39888765fe3e55674d5b6d18b9d5b65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641012"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="4cca3-102">&lt;param&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4cca3-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="4cca3-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4cca3-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cca3-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4cca3-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4cca3-105">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="4cca3-105">The name of a method parameter.</span></span> <span data-ttu-id="4cca3-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="4cca3-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="4cca3-107">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4cca3-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cca3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4cca3-108">Remarks</span></span>  
 <span data-ttu-id="4cca3-109">A marca \<param> deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="4cca3-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="4cca3-110">Para documentar vários parâmetros, use várias marcas \<param>.</span><span class="sxs-lookup"><span data-stu-id="4cca3-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="4cca3-111">O texto da marca \<param> será exibido no IntelliSense, o Pesquisador de Objetos e no relatório Web de comentários sobre código.</span><span class="sxs-lookup"><span data-stu-id="4cca3-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="4cca3-112">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="4cca3-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cca3-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4cca3-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4cca3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4cca3-114">See also</span></span>

- [<span data-ttu-id="4cca3-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4cca3-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4cca3-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="4cca3-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
