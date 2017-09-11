---
title: "&lt;value&gt; (Guia de programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <value>
dev_langs:
- CSharp
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: 12
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
ms.openlocfilehash: 71c8d5ab2e99291f05ef362960b0eeac969e9de1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="70f8f-102">&lt;value&gt; (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="70f8f-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="70f8f-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70f8f-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70f8f-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70f8f-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="70f8f-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="70f8f-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70f8f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="70f8f-106">Remarks</span></span>  
 <span data-ttu-id="70f8f-107">A marca \<value> permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="70f8f-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="70f8f-108">Observe que quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento do Visual Studio .NET, ele adicionará uma marca [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="70f8f-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="70f8f-109">Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="70f8f-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="70f8f-110">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="70f8f-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70f8f-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70f8f-111">Example</span></span>  
 <span data-ttu-id="70f8f-112">[!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="70f8f-112">[!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f8f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70f8f-113">See Also</span></span>  
 <span data-ttu-id="70f8f-114">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="70f8f-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="70f8f-115">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="70f8f-115">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

