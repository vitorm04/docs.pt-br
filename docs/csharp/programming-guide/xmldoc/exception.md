---
title: <exception>-Guia de programação C#
description: Saiba mais sobre a <exception> marca XML. Essa marca permite que você especifique quais exceções podem ser geradas e pode ser aplicada a métodos, propriedades, eventos e indexadores.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 22a28f3fe6de5a0db9aea0f1fd7963d4e6fcee05
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381730"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="9e1d8-104">\<exception>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="9e1d8-104">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e1d8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e1d8-105">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="9e1d8-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e1d8-106">Parameters</span></span>

- <span data-ttu-id="9e1d8-107">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="9e1d8-107">cref = " `member`"</span></span>

  <span data-ttu-id="9e1d8-108">Uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-108">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="9e1d8-109">O compilador verifica se a exceção apresentada existe e move o `member` para o nome de elemento canônico no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-109">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="9e1d8-110">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="9e1d8-110">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="9e1d8-111">Confira mais informações sobre como formatar `member` para fazer referência a um tipo genérico em [Como processar o Arquivo XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="9e1d8-111">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="9e1d8-112">Uma descrição da exceção.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-112">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e1d8-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e1d8-113">Remarks</span></span>

<span data-ttu-id="9e1d8-114">A `<exception>` marca permite especificar quais exceções podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-114">The `<exception>` tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="9e1d8-115">Essa marca pode ser aplicada às definições de métodos, propriedades, eventos e indexadores.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-115">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="9e1d8-116">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="9e1d8-117">Para obter mais informações sobre o tratamento de exceção, consulte [Exceções e tratamento de exceção](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e1d8-117">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="9e1d8-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e1d8-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="9e1d8-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e1d8-119">See also</span></span>

- [<span data-ttu-id="9e1d8-120">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="9e1d8-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="9e1d8-121">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="9e1d8-121">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
