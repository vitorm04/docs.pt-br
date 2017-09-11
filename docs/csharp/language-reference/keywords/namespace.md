---
title: "namespace (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
dev_langs:
- CSharp
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2cef3949d9a41db36406db059218f7a204172ea
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="namespace-c-reference"></a><span data-ttu-id="7f762-102">namespace (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7f762-102">namespace (C# Reference)</span></span>
<span data-ttu-id="7f762-103">A palavra-chave `namespace` é usada para declarar um escopo que contém um conjunto de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="7f762-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="7f762-104">Você pode usar um namespace para organizar elementos de código e criar tipos globalmente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="7f762-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 <span data-ttu-id="7f762-105">[!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f762-105">[!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f762-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f762-106">Remarks</span></span>  
 <span data-ttu-id="7f762-107">Dentro de um namespace, você pode declarar um ou mais dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="7f762-107">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="7f762-108">outro namespace</span><span class="sxs-lookup"><span data-stu-id="7f762-108">another namespace</span></span>  
  
-   [<span data-ttu-id="7f762-109">class</span><span class="sxs-lookup"><span data-stu-id="7f762-109">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="7f762-110">interface</span><span class="sxs-lookup"><span data-stu-id="7f762-110">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="7f762-111">struct</span><span class="sxs-lookup"><span data-stu-id="7f762-111">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="7f762-112">enum</span><span class="sxs-lookup"><span data-stu-id="7f762-112">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="7f762-113">delegate</span><span class="sxs-lookup"><span data-stu-id="7f762-113">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="7f762-114">Quer você declare explicitamente ou não um namespace em um arquivo de origem C#, o compilador adiciona um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="7f762-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="7f762-115">Este namespace sem nome, às vezes chamado de namespace global, está presente em todos os arquivos.</span><span class="sxs-lookup"><span data-stu-id="7f762-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="7f762-116">Qualquer identificador no namespace global está disponível para uso em um namespace nomeado.</span><span class="sxs-lookup"><span data-stu-id="7f762-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="7f762-117">Os namespaces implicitamente têm acesso público e não isso é modificável.</span><span class="sxs-lookup"><span data-stu-id="7f762-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="7f762-118">Para uma discussão sobre os modificadores de acesso que você pode atribuir a elementos em um namespace, consulte [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="7f762-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="7f762-119">É possível definir um namespace em duas ou mais declarações.</span><span class="sxs-lookup"><span data-stu-id="7f762-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="7f762-120">Por exemplo, o exemplo a seguir define duas classes como parte do namespace `MyCompany`:</span><span class="sxs-lookup"><span data-stu-id="7f762-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 <span data-ttu-id="7f762-121">[!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f762-121">[!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f762-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f762-122">Example</span></span>  
 <span data-ttu-id="7f762-123">O exemplo a seguir mostra como chamar um método estático em um namespace aninhado.</span><span class="sxs-lookup"><span data-stu-id="7f762-123">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 <span data-ttu-id="7f762-124">[!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f762-124">[!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="7f762-125">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="7f762-125">For More Information</span></span>  
 <span data-ttu-id="7f762-126">Para obter mais informações sobre o uso de namespaces, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="7f762-126">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="7f762-127">Namespaces</span><span class="sxs-lookup"><span data-stu-id="7f762-127">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="7f762-128">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="7f762-128">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="7f762-129">Como usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="7f762-129">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="7f762-130">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7f762-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f762-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f762-131">See Also</span></span>  
 <span data-ttu-id="7f762-132">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7f762-132">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7f762-133">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7f762-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7f762-134">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="7f762-134">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="7f762-135">[Palavras-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="7f762-135">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 [<span data-ttu-id="7f762-136">using</span><span class="sxs-lookup"><span data-stu-id="7f762-136">using</span></span>](../../../csharp/language-reference/keywords/using.md)

