---
title: Namespaces (Guia de Programação em C#)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: c4011092a6c605137053b544d4b9f14cce2fdb4c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624548"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="d5cf7-102">Namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d5cf7-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="d5cf7-103">Os namespaces são usados intensamente em programações de C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="d5cf7-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="d5cf7-104">Em primeiro lugar, o .NET Framework usa namespaces para organizar suas muitas classes, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d5cf7-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
<span data-ttu-id="d5cf7-105">`System` é um namespace e `Console` é uma classe nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="d5cf7-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="d5cf7-106">A palavra-chave `using` pode ser usada para que o nome completo não seja necessário, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5cf7-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
<span data-ttu-id="d5cf7-107">Para saber mais, confira [Diretiva using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="d5cf7-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="d5cf7-108">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="d5cf7-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="d5cf7-109">Use a palavra-chave [namespace](../../language-reference/keywords/namespace.md) para declarar um namespace, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5cf7-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

<span data-ttu-id="d5cf7-110">O nome do namespace deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.</span><span class="sxs-lookup"><span data-stu-id="d5cf7-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="d5cf7-111">Visão geral sobre namespaces</span><span class="sxs-lookup"><span data-stu-id="d5cf7-111">Namespaces Overview</span></span>  

<span data-ttu-id="d5cf7-112">Os namespaces têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="d5cf7-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="d5cf7-113">Eles organizam projetos de códigos grandes.</span><span class="sxs-lookup"><span data-stu-id="d5cf7-113">They organize large code projects.</span></span>  
- <span data-ttu-id="d5cf7-114">Eles são delimitados usando o operador `.`.</span><span class="sxs-lookup"><span data-stu-id="d5cf7-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="d5cf7-115">O `using directive` elimina a necessidade de especificar o nome do namespace para cada classe.</span><span class="sxs-lookup"><span data-stu-id="d5cf7-115">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="d5cf7-116">O namespace `global` é o namespace "raiz": `global::System` sempre fará referência ao namespace do .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="d5cf7-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="d5cf7-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d5cf7-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5cf7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5cf7-118">See Also</span></span>

- [<span data-ttu-id="d5cf7-119">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="d5cf7-119">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="d5cf7-120">Como usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="d5cf7-120">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="d5cf7-121">Como usar o My Namespace</span><span class="sxs-lookup"><span data-stu-id="d5cf7-121">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="d5cf7-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d5cf7-122">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="d5cf7-123">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="d5cf7-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="d5cf7-124">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="d5cf7-124">Namespace Keywords</span></span>](../../language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="d5cf7-125">Diretiva using</span><span class="sxs-lookup"><span data-stu-id="d5cf7-125">using Directive</span></span>](../../language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="d5cf7-126">Operador ::</span><span class="sxs-lookup"><span data-stu-id="d5cf7-126">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="d5cf7-127">. ??</span><span class="sxs-lookup"><span data-stu-id="d5cf7-127">. Operator</span></span>](../../language-reference/operators/member-access-operator.md)
>>>>>>> <span data-ttu-id="d5cf7-128">adicionar regras de nomenclatura de identificadores</span><span class="sxs-lookup"><span data-stu-id="d5cf7-128">add identifier naming rules</span></span>
