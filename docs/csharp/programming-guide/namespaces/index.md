---
title: Namespaces – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 893ac7bbfcfe159787789238c3142f34ac7ecf35
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423293"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="e576e-102">Namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e576e-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="e576e-103">Os namespaces são usados intensamente em programações de C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="e576e-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="e576e-104">Em primeiro lugar, o .NET Framework usa namespaces para organizar suas muitas classes, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e576e-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="e576e-105">`System` é um namespace e `Console` é uma classe nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="e576e-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="e576e-106">A palavra-chave `using` pode ser usada para que o nome completo não seja necessário, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e576e-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="e576e-107">Para saber mais, confira [Diretiva using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="e576e-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="e576e-108">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="e576e-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="e576e-109">Use a palavra-chave [namespace](../../language-reference/keywords/namespace.md) para declarar um namespace, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e576e-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="e576e-110">O nome do namespace deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.</span><span class="sxs-lookup"><span data-stu-id="e576e-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="e576e-111">Visão geral sobre namespaces</span><span class="sxs-lookup"><span data-stu-id="e576e-111">Namespaces Overview</span></span>  

<span data-ttu-id="e576e-112">Os namespaces têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e576e-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="e576e-113">Eles organizam projetos de códigos grandes.</span><span class="sxs-lookup"><span data-stu-id="e576e-113">They organize large code projects.</span></span>  
- <span data-ttu-id="e576e-114">Eles são delimitados usando o operador `.`.</span><span class="sxs-lookup"><span data-stu-id="e576e-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="e576e-115">A diretiva `using` elimina a necessidade de especificar o nome do namespace para cada classe.</span><span class="sxs-lookup"><span data-stu-id="e576e-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="e576e-116">O namespace `global` é o namespace "raiz": `global::System` sempre fará referência ao namespace do .NET <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="e576e-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="e576e-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e576e-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e576e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e576e-118">See also</span></span>

- [<span data-ttu-id="e576e-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e576e-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e576e-120">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="e576e-120">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="e576e-121">Como: usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="e576e-121">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="e576e-122">Como: usar o My Namespace</span><span class="sxs-lookup"><span data-stu-id="e576e-122">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="e576e-123">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="e576e-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="e576e-124">Diretiva using</span><span class="sxs-lookup"><span data-stu-id="e576e-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="e576e-125">:: ??</span><span class="sxs-lookup"><span data-stu-id="e576e-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)
