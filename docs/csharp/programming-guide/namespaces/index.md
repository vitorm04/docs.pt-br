---
title: Namespaces – Guia de Programação em C#
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937608"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="10beb-102">Namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="10beb-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="10beb-103">Os namespaces são usados intensamente em programações de C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="10beb-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="10beb-104">Primeiro, .NET usa namespaces para organizar suas muitas classes, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="10beb-104">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="10beb-105"><xref:System> é um namespace e <xref:System.Console> é uma classe nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="10beb-105"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="10beb-106">A palavra-chave `using` pode ser usada para que o nome completo não seja necessário, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="10beb-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

<span data-ttu-id="10beb-107">Para saber mais, confira [Diretiva using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="10beb-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="10beb-108">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="10beb-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="10beb-109">Use a palavra-chave [namespace](../../language-reference/keywords/namespace.md) para declarar um namespace, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="10beb-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="10beb-110">O nome do namespace deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.</span><span class="sxs-lookup"><span data-stu-id="10beb-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="10beb-111">Visão geral do Namespaces</span><span class="sxs-lookup"><span data-stu-id="10beb-111">Namespaces overview</span></span>

<span data-ttu-id="10beb-112">Os namespaces têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="10beb-112">Namespaces have the following properties:</span></span>

- <span data-ttu-id="10beb-113">Eles organizam projetos de códigos grandes.</span><span class="sxs-lookup"><span data-stu-id="10beb-113">They organize large code projects.</span></span>
- <span data-ttu-id="10beb-114">Eles são delimitados usando o operador `.`.</span><span class="sxs-lookup"><span data-stu-id="10beb-114">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="10beb-115">A diretiva `using` elimina a necessidade de especificar o nome do namespace para cada classe.</span><span class="sxs-lookup"><span data-stu-id="10beb-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="10beb-116">O namespace `global` é o namespace "raiz": `global::System` sempre fará referência ao namespace do .NET <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="10beb-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="10beb-117">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="10beb-117">C# language specification</span></span>

<span data-ttu-id="10beb-118">Para saber mais, confira a seção [Namespaces](~/_csharplang/spec/namespaces.md) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="10beb-118">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10beb-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="10beb-119">See also</span></span>

- [<span data-ttu-id="10beb-120">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="10beb-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="10beb-121">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="10beb-121">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="10beb-122">Como usar o My Namespace</span><span class="sxs-lookup"><span data-stu-id="10beb-122">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="10beb-123">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="10beb-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="10beb-124">Diretiva using</span><span class="sxs-lookup"><span data-stu-id="10beb-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="10beb-125">:: Operador</span><span class="sxs-lookup"><span data-stu-id="10beb-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
