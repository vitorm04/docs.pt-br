---
title: Namespaces – Guia de Programação em C#
description: Saiba mais sobre namespaces em programação em C#. Consulte uma visão geral das propriedades do namespace e exiba recursos adicionais.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 41a666fd5f368e6990e08a36700e18f648939213
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440335"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="8b9bb-104">Namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8b9bb-104">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="8b9bb-105">Os namespaces são usados intensamente em programações de C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="8b9bb-105">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="8b9bb-106">Primeiro, o .NET usa namespaces para organizar suas várias classes, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8b9bb-106">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="8b9bb-107"><xref:System> é um namespace e <xref:System.Console> é uma classe nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="8b9bb-107"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="8b9bb-108">A palavra-chave `using` pode ser usada para que o nome completo não seja necessário, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8b9bb-108">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="8b9bb-109">Para saber mais, confira [Diretiva using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="8b9bb-109">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="8b9bb-110">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="8b9bb-110">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="8b9bb-111">Use a palavra-chave [namespace](../../language-reference/keywords/namespace.md) para declarar um namespace, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8b9bb-111">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="8b9bb-112">O nome do namespace deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.</span><span class="sxs-lookup"><span data-stu-id="8b9bb-112">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="8b9bb-113">Visão geral dos namespaces</span><span class="sxs-lookup"><span data-stu-id="8b9bb-113">Namespaces overview</span></span>

<span data-ttu-id="8b9bb-114">Os namespaces têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8b9bb-114">Namespaces have the following properties:</span></span>

- <span data-ttu-id="8b9bb-115">Eles organizam projetos de códigos grandes.</span><span class="sxs-lookup"><span data-stu-id="8b9bb-115">They organize large code projects.</span></span>
- <span data-ttu-id="8b9bb-116">Eles são delimitados usando o operador `.`.</span><span class="sxs-lookup"><span data-stu-id="8b9bb-116">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="8b9bb-117">A diretiva `using` elimina a necessidade de especificar o nome do namespace para cada classe.</span><span class="sxs-lookup"><span data-stu-id="8b9bb-117">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="8b9bb-118">O namespace `global` é o namespace "raiz": `global::System` sempre fará referência ao namespace do .NET <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="8b9bb-118">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8b9bb-119">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8b9bb-119">C# language specification</span></span>

<span data-ttu-id="8b9bb-120">Para saber mais, confira a seção [Namespaces](~/_csharplang/spec/namespaces.md) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8b9bb-120">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b9bb-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b9bb-121">See also</span></span>

- [<span data-ttu-id="8b9bb-122">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8b9bb-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8b9bb-123">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="8b9bb-123">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="8b9bb-124">Como usar o My Namespace</span><span class="sxs-lookup"><span data-stu-id="8b9bb-124">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="8b9bb-125">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="8b9bb-125">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="8b9bb-126">Diretiva de uso</span><span class="sxs-lookup"><span data-stu-id="8b9bb-126">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="8b9bb-127">Operador::</span><span class="sxs-lookup"><span data-stu-id="8b9bb-127">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
