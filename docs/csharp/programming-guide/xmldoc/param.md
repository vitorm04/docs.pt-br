---
title: "&lt;param&gt; (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
dev_langs:
- CSharp
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1076405d60c85540eeaeba39821bd20bc628030d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="b45f3-102">&lt;param&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b45f3-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b45f3-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b45f3-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b45f3-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b45f3-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b45f3-105">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="b45f3-105">The name of a method parameter.</span></span> <span data-ttu-id="b45f3-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="b45f3-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="b45f3-107">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b45f3-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b45f3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b45f3-108">Remarks</span></span>  
 <span data-ttu-id="b45f3-109">A marca \<param> deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="b45f3-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="b45f3-110">Para documentar vários parâmetros, use várias marcas \<param>.</span><span class="sxs-lookup"><span data-stu-id="b45f3-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="b45f3-111">O texto da marca \<param> será exibido no IntelliSense, o Pesquisador de Objetos e no relatório Web de comentários sobre código.</span><span class="sxs-lookup"><span data-stu-id="b45f3-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="b45f3-112">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="b45f3-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b45f3-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b45f3-113">Example</span></span>  
 <span data-ttu-id="b45f3-114">[!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b45f3-114">[!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45f3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b45f3-115">See Also</span></span>  
 <span data-ttu-id="b45f3-116">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b45f3-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="b45f3-117">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="b45f3-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

