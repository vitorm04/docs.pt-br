---
title: Namespaces (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334344"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="2462a-102">Namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2462a-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="2462a-103">Os namespaces são usados intensamente em programações de C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="2462a-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="2462a-104">Em primeiro lugar, o .NET Framework usa namespaces para organizar suas muitas classes, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2462a-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="2462a-105">`System` é um namespace e `Console` é uma classe nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="2462a-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="2462a-106">A palavra-chave `using` pode ser usada para que o nome completo não seja necessário, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2462a-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="2462a-107">Consulte [Diretiva using](../../../csharp/language-reference/keywords/using-directive.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2462a-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="2462a-108">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="2462a-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="2462a-109">Use a palavra-chave [namespace](../../../csharp/language-reference/keywords/namespace.md) para declarar um namespace, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2462a-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="2462a-110">Visão geral sobre namespaces</span><span class="sxs-lookup"><span data-stu-id="2462a-110">Namespaces Overview</span></span>  
 <span data-ttu-id="2462a-111">Os namespaces têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="2462a-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="2462a-112">Eles organizam projetos de códigos grandes.</span><span class="sxs-lookup"><span data-stu-id="2462a-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="2462a-113">Eles são delimitados usando o operador `.`.</span><span class="sxs-lookup"><span data-stu-id="2462a-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="2462a-114">O `using directive` elimina a necessidade de especificar o nome do namespace para cada classe.</span><span class="sxs-lookup"><span data-stu-id="2462a-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="2462a-115">O namespace `global` é o namespace "raiz": `global::System` sempre fará referência ao namespace do .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="2462a-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2462a-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="2462a-116">Related Sections</span></span>  
 <span data-ttu-id="2462a-117">Consulte os tópicos a seguir para obter mais informações sobre namespaces:</span><span class="sxs-lookup"><span data-stu-id="2462a-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="2462a-118">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="2462a-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="2462a-119">Como usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="2462a-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="2462a-120">Como usar o My Namespace</span><span class="sxs-lookup"><span data-stu-id="2462a-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="2462a-121">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2462a-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2462a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2462a-122">See Also</span></span>  
 [<span data-ttu-id="2462a-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2462a-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2462a-124">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="2462a-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="2462a-125">Diretiva using</span><span class="sxs-lookup"><span data-stu-id="2462a-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="2462a-126">Operador ::</span><span class="sxs-lookup"><span data-stu-id="2462a-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="2462a-127">. ??</span><span class="sxs-lookup"><span data-stu-id="2462a-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
