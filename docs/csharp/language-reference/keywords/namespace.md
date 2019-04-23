---
title: Palavra-chave namespace – Referência de C#
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 4859c361b3321c1144204f63896152694f6ac5c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148753"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="63f2d-102">namespace (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="63f2d-102">namespace (C# Reference)</span></span>

<span data-ttu-id="63f2d-103">A palavra-chave `namespace` é usada para declarar um escopo que contém um conjunto de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="63f2d-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="63f2d-104">Você pode usar um namespace para organizar elementos de código e criar tipos globalmente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="63f2d-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="63f2d-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="63f2d-105">Remarks</span></span>

<span data-ttu-id="63f2d-106">Dentro de um namespace, é possível declarar zero ou mais dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="63f2d-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="63f2d-107">outro namespace</span><span class="sxs-lookup"><span data-stu-id="63f2d-107">another namespace</span></span>

- [<span data-ttu-id="63f2d-108">class</span><span class="sxs-lookup"><span data-stu-id="63f2d-108">class</span></span>](class.md)

- [<span data-ttu-id="63f2d-109">interface</span><span class="sxs-lookup"><span data-stu-id="63f2d-109">interface</span></span>](interface.md)

- [<span data-ttu-id="63f2d-110">struct</span><span class="sxs-lookup"><span data-stu-id="63f2d-110">struct</span></span>](struct.md)

- [<span data-ttu-id="63f2d-111">enum</span><span class="sxs-lookup"><span data-stu-id="63f2d-111">enum</span></span>](enum.md)

- [<span data-ttu-id="63f2d-112">delegate</span><span class="sxs-lookup"><span data-stu-id="63f2d-112">delegate</span></span>](delegate.md)

<span data-ttu-id="63f2d-113">Quer você declare explicitamente ou não um namespace em um arquivo de origem C#, o compilador adiciona um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="63f2d-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="63f2d-114">Este namespace sem nome, às vezes chamado de namespace global, está presente em todos os arquivos.</span><span class="sxs-lookup"><span data-stu-id="63f2d-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="63f2d-115">Qualquer identificador no namespace global está disponível para uso em um namespace nomeado.</span><span class="sxs-lookup"><span data-stu-id="63f2d-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="63f2d-116">Os namespaces implicitamente têm acesso público e não isso é modificável.</span><span class="sxs-lookup"><span data-stu-id="63f2d-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="63f2d-117">Para uma discussão sobre os modificadores de acesso que você pode atribuir a elementos em um namespace, consulte [Modificadores de acesso](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="63f2d-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="63f2d-118">É possível definir um namespace em duas ou mais declarações.</span><span class="sxs-lookup"><span data-stu-id="63f2d-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="63f2d-119">Por exemplo, o exemplo a seguir define duas classes como parte do namespace `MyCompany`:</span><span class="sxs-lookup"><span data-stu-id="63f2d-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="63f2d-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63f2d-120">Example</span></span>

<span data-ttu-id="63f2d-121">O exemplo a seguir mostra como chamar um método estático em um namespace aninhado.</span><span class="sxs-lookup"><span data-stu-id="63f2d-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a><span data-ttu-id="63f2d-122">Recursos relacionados</span><span class="sxs-lookup"><span data-stu-id="63f2d-122">Related resources</span></span>

<span data-ttu-id="63f2d-123">Para obter mais informações sobre o uso de namespaces, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="63f2d-123">For more information about using namespaces, see the following topics:</span></span>

- [<span data-ttu-id="63f2d-124">Namespaces</span><span class="sxs-lookup"><span data-stu-id="63f2d-124">Namespaces</span></span>](../../programming-guide/namespaces/index.md)

- [<span data-ttu-id="63f2d-125">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="63f2d-125">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)

- [<span data-ttu-id="63f2d-126">Como: usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="63f2d-126">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="63f2d-127">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="63f2d-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="63f2d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63f2d-128">See also</span></span>

- [<span data-ttu-id="63f2d-129">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="63f2d-129">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="63f2d-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="63f2d-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="63f2d-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="63f2d-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="63f2d-132">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="63f2d-132">Namespace Keywords</span></span>](namespace-keywords.md)
- [<span data-ttu-id="63f2d-133">using</span><span class="sxs-lookup"><span data-stu-id="63f2d-133">using</span></span>](using-directive.md)
- [<span data-ttu-id="63f2d-134">using static</span><span class="sxs-lookup"><span data-stu-id="63f2d-134">using static</span></span>](using-static.md)