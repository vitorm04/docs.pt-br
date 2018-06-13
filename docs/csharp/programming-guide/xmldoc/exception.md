---
title: '&lt;exceção&gt; (Guia de programação em C#)'
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: eca61416077896c9fa7d5828bbab79b399ad69d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332654"
---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="49a65-102">&lt;exceção&gt; (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="49a65-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="49a65-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49a65-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49a65-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49a65-104">Parameters</span></span>  
 <span data-ttu-id="49a65-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="49a65-105">cref = " `member`"</span></span>  
 <span data-ttu-id="49a65-106">Uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="49a65-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="49a65-107">O compilador verifica se a exceção apresentada existe e move o `member` para o nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="49a65-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="49a65-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="49a65-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="49a65-109">Para obter mais informações sobre como criar uma referência cref para um tipo genérico, consulte [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="49a65-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="49a65-110">Uma descrição da exceção.</span><span class="sxs-lookup"><span data-stu-id="49a65-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49a65-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="49a65-111">Remarks</span></span>  
 <span data-ttu-id="49a65-112">A marca \<exception> permite que você especifique quais exceções podem ser lançadas.</span><span class="sxs-lookup"><span data-stu-id="49a65-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="49a65-113">Essa marca pode ser aplicada às definições de métodos, propriedades, eventos e indexadores.</span><span class="sxs-lookup"><span data-stu-id="49a65-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="49a65-114">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="49a65-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="49a65-115">Para obter mais informações sobre o tratamento de exceção, consulte [Exceções e tratamento de exceção](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="49a65-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49a65-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="49a65-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="49a65-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49a65-117">See Also</span></span>  
 [<span data-ttu-id="49a65-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="49a65-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="49a65-119">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="49a65-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
