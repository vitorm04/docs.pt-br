---
title: <exception>- Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789799"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="02ac5-102">\<> exceção (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="02ac5-102">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="02ac5-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02ac5-103">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="02ac5-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="02ac5-104">Parameters</span></span>

- <span data-ttu-id="02ac5-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="02ac5-105">cref = " `member`"</span></span>

  <span data-ttu-id="02ac5-106">Uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="02ac5-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="02ac5-107">O compilador verifica se a exceção apresentada existe e move o `member` para o nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="02ac5-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="02ac5-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="02ac5-108">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="02ac5-109">Confira mais informações sobre como formatar `member` para fazer referência a um tipo genérico em [Como processar o Arquivo XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="02ac5-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="02ac5-110">Uma descrição da exceção.</span><span class="sxs-lookup"><span data-stu-id="02ac5-110">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="02ac5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="02ac5-111">Remarks</span></span>

<span data-ttu-id="02ac5-112">A marca \<exception> permite que você especifique quais exceções podem ser lançadas.</span><span class="sxs-lookup"><span data-stu-id="02ac5-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="02ac5-113">Essa marca pode ser aplicada às definições de métodos, propriedades, eventos e indexadores.</span><span class="sxs-lookup"><span data-stu-id="02ac5-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="02ac5-114">Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="02ac5-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="02ac5-115">Para obter mais informações sobre o tratamento de exceção, consulte [Exceções e tratamento de exceção](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="02ac5-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="02ac5-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02ac5-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="02ac5-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="02ac5-117">See also</span></span>

- [<span data-ttu-id="02ac5-118">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="02ac5-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="02ac5-119">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="02ac5-119">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
