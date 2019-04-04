---
title: Namespaces – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 3e05e18225b198e9e34b4b96717cc813dab836c7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971267"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="e6b2a-102">Namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e6b2a-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="e6b2a-103">Os namespaces são usados intensamente em programações de C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="e6b2a-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="e6b2a-104">Em primeiro lugar, o .NET Framework usa namespaces para organizar suas muitas classes, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e6b2a-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="e6b2a-105">`System` é um namespace e `Console` é uma classe nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="e6b2a-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="e6b2a-106">A palavra-chave `using` pode ser usada para que o nome completo não seja necessário, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6b2a-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="e6b2a-107">Para saber mais, confira [Diretiva using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="e6b2a-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="e6b2a-108">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="e6b2a-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="e6b2a-109">Use a palavra-chave [namespace](../../language-reference/keywords/namespace.md) para declarar um namespace, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6b2a-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="e6b2a-110">O nome do namespace deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.</span><span class="sxs-lookup"><span data-stu-id="e6b2a-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="e6b2a-111">Visão geral sobre namespaces</span><span class="sxs-lookup"><span data-stu-id="e6b2a-111">Namespaces Overview</span></span>  

<span data-ttu-id="e6b2a-112">Os namespaces têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e6b2a-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="e6b2a-113">Eles organizam projetos de códigos grandes.</span><span class="sxs-lookup"><span data-stu-id="e6b2a-113">They organize large code projects.</span></span>  
- <span data-ttu-id="e6b2a-114">Eles são delimitados usando o operador `.`.</span><span class="sxs-lookup"><span data-stu-id="e6b2a-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="e6b2a-115">A diretiva `using` elimina a necessidade de especificar o nome do namespace para cada classe.</span><span class="sxs-lookup"><span data-stu-id="e6b2a-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="e6b2a-116">O namespace `global` é o namespace "raiz": `global::System` sempre fará referência ao namespace do .NET <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="e6b2a-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="e6b2a-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e6b2a-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b2a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6b2a-118">See also</span></span>

- [<span data-ttu-id="e6b2a-119">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="e6b2a-119">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="e6b2a-120">Como: usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="e6b2a-120">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="e6b2a-121">Como: usar o My Namespace</span><span class="sxs-lookup"><span data-stu-id="e6b2a-121">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="e6b2a-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e6b2a-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e6b2a-123">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="e6b2a-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="e6b2a-124">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="e6b2a-124">Namespace Keywords</span></span>](../../language-reference/keywords/namespace-keywords.md)
- [<span data-ttu-id="e6b2a-125">Diretiva using</span><span class="sxs-lookup"><span data-stu-id="e6b2a-125">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="e6b2a-126">:: ??</span><span class="sxs-lookup"><span data-stu-id="e6b2a-126">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="e6b2a-127">. ??</span><span class="sxs-lookup"><span data-stu-id="e6b2a-127">. Operator</span></span>](../../language-reference/operators/member-access-operator.md)
