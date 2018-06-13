---
title: namespace (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 343cce85dd235532fbe3fc90af0a785f48518db7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276013"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="f9dc9-102">namespace (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f9dc9-102">namespace (C# Reference)</span></span>
<span data-ttu-id="f9dc9-103">A palavra-chave `namespace` é usada para declarar um escopo que contém um conjunto de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="f9dc9-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="f9dc9-104">Você pode usar um namespace para organizar elementos de código e criar tipos globalmente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="f9dc9-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="f9dc9-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9dc9-105">Remarks</span></span>  
 <span data-ttu-id="f9dc9-106">Dentro de um namespace, você pode declarar um ou mais dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="f9dc9-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="f9dc9-107">outro namespace</span><span class="sxs-lookup"><span data-stu-id="f9dc9-107">another namespace</span></span>  
  
-   [<span data-ttu-id="f9dc9-108">class</span><span class="sxs-lookup"><span data-stu-id="f9dc9-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="f9dc9-109">interface</span><span class="sxs-lookup"><span data-stu-id="f9dc9-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="f9dc9-110">struct</span><span class="sxs-lookup"><span data-stu-id="f9dc9-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="f9dc9-111">enum</span><span class="sxs-lookup"><span data-stu-id="f9dc9-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="f9dc9-112">delegate</span><span class="sxs-lookup"><span data-stu-id="f9dc9-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="f9dc9-113">Quer você declare explicitamente ou não um namespace em um arquivo de origem C#, o compilador adiciona um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="f9dc9-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="f9dc9-114">Este namespace sem nome, às vezes chamado de namespace global, está presente em todos os arquivos.</span><span class="sxs-lookup"><span data-stu-id="f9dc9-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="f9dc9-115">Qualquer identificador no namespace global está disponível para uso em um namespace nomeado.</span><span class="sxs-lookup"><span data-stu-id="f9dc9-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="f9dc9-116">Os namespaces implicitamente têm acesso público e não isso é modificável.</span><span class="sxs-lookup"><span data-stu-id="f9dc9-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="f9dc9-117">Para uma discussão sobre os modificadores de acesso que você pode atribuir a elementos em um namespace, consulte [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f9dc9-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="f9dc9-118">É possível definir um namespace em duas ou mais declarações.</span><span class="sxs-lookup"><span data-stu-id="f9dc9-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="f9dc9-119">Por exemplo, o exemplo a seguir define duas classes como parte do namespace `MyCompany`:</span><span class="sxs-lookup"><span data-stu-id="f9dc9-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="f9dc9-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9dc9-120">Example</span></span>  
 <span data-ttu-id="f9dc9-121">O exemplo a seguir mostra como chamar um método estático em um namespace aninhado.</span><span class="sxs-lookup"><span data-stu-id="f9dc9-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="f9dc9-122">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="f9dc9-122">For More Information</span></span>  
 <span data-ttu-id="f9dc9-123">Para obter mais informações sobre o uso de namespaces, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="f9dc9-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="f9dc9-124">Namespaces</span><span class="sxs-lookup"><span data-stu-id="f9dc9-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="f9dc9-125">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="f9dc9-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="f9dc9-126">Como usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="f9dc9-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f9dc9-127">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f9dc9-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9dc9-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9dc9-128">See Also</span></span>  
 [<span data-ttu-id="f9dc9-129">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f9dc9-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f9dc9-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f9dc9-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f9dc9-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f9dc9-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f9dc9-132">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="f9dc9-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="f9dc9-133">using</span><span class="sxs-lookup"><span data-stu-id="f9dc9-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
