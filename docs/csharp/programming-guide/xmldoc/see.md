---
title: "&lt;see&gt; (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 959da56269081ebee036c620e535185609c5bff3
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="87143-102">&lt;see&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="87143-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="87143-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87143-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87143-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87143-104">Parameters</span></span>  
 <span data-ttu-id="87143-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="87143-105">cref = " `member`"</span></span>  
 <span data-ttu-id="87143-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="87143-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="87143-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.Coloque o *membro* entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="87143-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87143-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="87143-108">Remarks</span></span>  
 <span data-ttu-id="87143-109">Use a marca \<see> para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="87143-109">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="87143-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) para indicar que o texto deve ser colocado em uma seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="87143-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="87143-111">Use o [atributo cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) para criar hyperlinks internos para páginas de documentação para elementos de código.</span><span class="sxs-lookup"><span data-stu-id="87143-111">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="87143-112">Compile com [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="87143-112">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="87143-113">O exemplo a seguir mostra uma marca \<see> dentro de uma seção de resumo.</span><span class="sxs-lookup"><span data-stu-id="87143-113">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="87143-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87143-114">See Also</span></span>  
 [<span data-ttu-id="87143-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="87143-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="87143-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="87143-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
