---
title: tipo parcial – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 7af43a25f88ff0a53e5fa257b13bb1dc8a6d55eb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422606"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="29e47-102">tipo parcial (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="29e47-102">partial type (C# Reference)</span></span>

<span data-ttu-id="29e47-103">Definições de tipo parcial permitem que a definição de uma classe, struct ou interface seja dividida em vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="29e47-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="29e47-104">Em *File1.cs*:</span><span class="sxs-lookup"><span data-stu-id="29e47-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="29e47-105">Em *File2.cs*, a declaração:</span><span class="sxs-lookup"><span data-stu-id="29e47-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="29e47-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="29e47-106">Remarks</span></span>

<span data-ttu-id="29e47-107">Dividir um tipo de classe, struct ou interface em vários arquivos pode ser útil quando você está trabalhando com projetos grandes ou com o código gerado automaticamente, como o código fornecido pelo [Designer de Formulários do Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="29e47-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="29e47-108">Um tipo parcial pode conter um [método parcial](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="29e47-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="29e47-109">Para obter mais informações, consulte [Classes parciais e métodos](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="29e47-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="29e47-110">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="29e47-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="29e47-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29e47-111">See also</span></span>

- [<span data-ttu-id="29e47-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="29e47-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="29e47-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="29e47-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="29e47-114">Modificadores</span><span class="sxs-lookup"><span data-stu-id="29e47-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="29e47-115">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="29e47-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
