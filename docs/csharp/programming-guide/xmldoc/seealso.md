---
title: '&lt;seealso&gt; (Guia de Programação em C#)'
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
ms.openlocfilehash: e3c9d68884e5cd4f5a4f81580f60cdde775458a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349129"
---
# <a name="ltseealsogt-c-programming-guide"></a><span data-ttu-id="6d013-102">&lt;seealso&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6d013-102">&lt;seealso&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="6d013-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d013-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d013-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d013-104">Parameters</span></span>  
 <span data-ttu-id="6d013-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="6d013-105">cref = " `member`"</span></span>  
 <span data-ttu-id="6d013-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="6d013-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="6d013-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.`member`</span><span class="sxs-lookup"><span data-stu-id="6d013-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="6d013-108">deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="6d013-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="6d013-109">Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [ \<consulte>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="6d013-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d013-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d013-110">Remarks</span></span>  
 <span data-ttu-id="6d013-111">A marca \<seealso > permite especificar o texto que você quer que seja exibido na seção Ver também.</span><span class="sxs-lookup"><span data-stu-id="6d013-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="6d013-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="6d013-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="6d013-113">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6d013-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d013-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d013-114">Example</span></span>  
 <span data-ttu-id="6d013-115">Consulte [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) para obter um exemplo sobre o uso de \<seealso>.</span><span class="sxs-lookup"><span data-stu-id="6d013-115">See [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d013-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d013-116">See Also</span></span>  
 [<span data-ttu-id="6d013-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6d013-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d013-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="6d013-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
