---
title: Palavra-chave checked – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713702"
---
# <a name="checked-c-reference"></a><span data-ttu-id="2661f-102">checked (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="2661f-102">checked (C# Reference)</span></span>

<span data-ttu-id="2661f-103">A palavra-chave `checked` é usada para habilitar explicitamente a verificação estouro para conversões e operações aritméticas de tipo integral.</span><span class="sxs-lookup"><span data-stu-id="2661f-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="2661f-104">Por padrão, uma expressão que contém somente valores constantes causa um erro do compilador se a expressão produzir um valor fora do intervalo do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="2661f-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="2661f-105">Se a expressão contiver um ou mais valores não constantes, o compilador não detectará o estouro.</span><span class="sxs-lookup"><span data-stu-id="2661f-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="2661f-106">Avaliar a expressão atribuída a `i2` no exemplo a seguir não causa um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="2661f-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="2661f-107">Por padrão, essas expressões não constantes não são verificados quanto ao estouro em tempo de execução e não geram exceções de estouro.</span><span class="sxs-lookup"><span data-stu-id="2661f-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="2661f-108">O exemplo anterior exibe -2,147,483,639 como a soma de dois números inteiros positivos.</span><span class="sxs-lookup"><span data-stu-id="2661f-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="2661f-109">A verificação de estouro pode ser habilitada por opções do compilador, configuração do ambiente ou uso da palavra-chave `checked`.</span><span class="sxs-lookup"><span data-stu-id="2661f-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="2661f-110">Os exemplos a seguir demonstram como usar uma expressão `checked` ou um bloco `checked` para detectar o estouro produzido pela soma anterior no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2661f-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="2661f-111">Os dois exemplos geram uma exceção de estouro.</span><span class="sxs-lookup"><span data-stu-id="2661f-111">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="2661f-112">A palavra-chave [unchecked](./unchecked.md) pode ser usada para impedir a verificação de estouro.</span><span class="sxs-lookup"><span data-stu-id="2661f-112">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="2661f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2661f-113">Example</span></span>

<span data-ttu-id="2661f-114">Este exemplo mostra como usar `checked` para habilitar a verificação de estouro em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2661f-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="2661f-115">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2661f-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2661f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="2661f-116">See also</span></span>

- [<span data-ttu-id="2661f-117">C# Referência</span><span class="sxs-lookup"><span data-stu-id="2661f-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2661f-118">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="2661f-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2661f-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="2661f-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2661f-120">Checked e unchecked</span><span class="sxs-lookup"><span data-stu-id="2661f-120">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="2661f-121">desmarcado</span><span class="sxs-lookup"><span data-stu-id="2661f-121">unchecked</span></span>](./unchecked.md)
