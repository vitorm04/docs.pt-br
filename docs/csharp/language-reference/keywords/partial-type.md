---
description: tipo parcial – Referência em C#
title: tipo parcial – Referência em C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 4e73b34390143a2ac9b839e1da79b7894232c4b4
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91437879"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="0ccdb-103">tipo parcial (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="0ccdb-103">partial type (C# Reference)</span></span>

<span data-ttu-id="0ccdb-104">As definições de tipo parcial permitem que a definição de uma classe, estrutura, interface ou registro seja dividida em vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="0ccdb-104">Partial type definitions allow for the definition of a class, struct, interface, or record to be split into multiple files.</span></span>

<span data-ttu-id="0ccdb-105">Em *file1.cs*:</span><span class="sxs-lookup"><span data-stu-id="0ccdb-105">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="0ccdb-106">Em *file2.cs* a declaração:</span><span class="sxs-lookup"><span data-stu-id="0ccdb-106">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="0ccdb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ccdb-107">Remarks</span></span>

<span data-ttu-id="0ccdb-108">Dividir um tipo de classe, struct ou interface em vários arquivos pode ser útil quando você está trabalhando com projetos grandes ou com o código gerado automaticamente, como o código fornecido pelo [Designer de Formulários do Windows](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time).</span><span class="sxs-lookup"><span data-stu-id="0ccdb-108">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time).</span></span> <span data-ttu-id="0ccdb-109">Um tipo parcial pode conter um [método parcial](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ccdb-109">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="0ccdb-110">Para obter mais informações, consulte [Classes parciais e métodos](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0ccdb-110">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0ccdb-111">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0ccdb-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0ccdb-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ccdb-112">See also</span></span>

- [<span data-ttu-id="0ccdb-113">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="0ccdb-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0ccdb-114">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="0ccdb-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0ccdb-115">Modificadores</span><span class="sxs-lookup"><span data-stu-id="0ccdb-115">Modifiers</span></span>](index.md)
- [<span data-ttu-id="0ccdb-116">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="0ccdb-116">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
