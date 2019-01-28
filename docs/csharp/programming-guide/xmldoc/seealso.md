---
title: '&lt;seealso&gt; – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e75480db9aebdeb2199694168abf4f774773b9c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543536"
---
# <a name="ltseealsogt-c-programming-guide"></a><span data-ttu-id="b79b7-102">&lt;seealso&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b79b7-102">&lt;seealso&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b79b7-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b79b7-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b79b7-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b79b7-104">Parameters</span></span>  
 <span data-ttu-id="b79b7-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="b79b7-105">cref = " `member`"</span></span>  
 <span data-ttu-id="b79b7-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="b79b7-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="b79b7-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.`member`</span><span class="sxs-lookup"><span data-stu-id="b79b7-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="b79b7-108">deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="b79b7-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="b79b7-109">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [ \<consulte>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="b79b7-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b79b7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b79b7-110">Remarks</span></span>  
 <span data-ttu-id="b79b7-111">A marca \<seealso > permite especificar o texto que você quer que seja exibido na seção Ver também.</span><span class="sxs-lookup"><span data-stu-id="b79b7-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="b79b7-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="b79b7-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="b79b7-113">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="b79b7-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b79b7-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b79b7-114">Example</span></span>  
 <span data-ttu-id="b79b7-115">Consulte [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) para obter um exemplo sobre o uso de \<seealso>.</span><span class="sxs-lookup"><span data-stu-id="b79b7-115">See [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79b7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b79b7-116">See also</span></span>

- [<span data-ttu-id="b79b7-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b79b7-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b79b7-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="b79b7-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
