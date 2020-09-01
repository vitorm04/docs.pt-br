---
description: Palavra-chave namespace – Referência de C#
title: Palavra-chave namespace – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: a6cfd1c3d37cbdef1f0dd72ddca85ce91f2e183b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139574"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="a5030-103">namespace (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a5030-103">namespace (C# Reference)</span></span>

<span data-ttu-id="a5030-104">A palavra-chave `namespace` é usada para declarar um escopo que contém um conjunto de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="a5030-104">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="a5030-105">Você pode usar um namespace para organizar elementos de código e criar tipos globalmente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="a5030-105">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="a5030-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5030-106">Remarks</span></span>

<span data-ttu-id="a5030-107">Dentro de um namespace, é possível declarar zero ou mais dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="a5030-107">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="a5030-108">outro namespace</span><span class="sxs-lookup"><span data-stu-id="a5030-108">another namespace</span></span>

- [<span data-ttu-id="a5030-109">class</span><span class="sxs-lookup"><span data-stu-id="a5030-109">class</span></span>](class.md)

- [<span data-ttu-id="a5030-110">interface</span><span class="sxs-lookup"><span data-stu-id="a5030-110">interface</span></span>](interface.md)

- [<span data-ttu-id="a5030-111">struct</span><span class="sxs-lookup"><span data-stu-id="a5030-111">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="a5030-112">enumera</span><span class="sxs-lookup"><span data-stu-id="a5030-112">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="a5030-113">delegate</span><span class="sxs-lookup"><span data-stu-id="a5030-113">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="a5030-114">Quer você declare explicitamente ou não um namespace em um arquivo de origem C#, o compilador adiciona um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="a5030-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="a5030-115">Este namespace sem nome, às vezes chamado de namespace global, está presente em todos os arquivos.</span><span class="sxs-lookup"><span data-stu-id="a5030-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="a5030-116">Qualquer identificador no namespace global está disponível para uso em um namespace nomeado.</span><span class="sxs-lookup"><span data-stu-id="a5030-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="a5030-117">Os namespaces implicitamente têm acesso público e não isso é modificável.</span><span class="sxs-lookup"><span data-stu-id="a5030-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="a5030-118">Para uma discussão sobre os modificadores de acesso que você pode atribuir a elementos em um namespace, consulte [Modificadores de acesso](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="a5030-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="a5030-119">É possível definir um namespace em duas ou mais declarações.</span><span class="sxs-lookup"><span data-stu-id="a5030-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="a5030-120">Por exemplo, o exemplo a seguir define duas classes como parte do namespace `MyCompany`:</span><span class="sxs-lookup"><span data-stu-id="a5030-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="a5030-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5030-121">Example</span></span>

<span data-ttu-id="a5030-122">O exemplo a seguir mostra como chamar um método estático em um namespace aninhado.</span><span class="sxs-lookup"><span data-stu-id="a5030-122">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="a5030-123">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a5030-123">C# language specification</span></span>

<span data-ttu-id="a5030-124">Para saber mais, confira a seção [Namespaces](~/_csharplang/spec/namespaces.md) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a5030-124">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5030-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5030-125">See also</span></span>

- [<span data-ttu-id="a5030-126">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a5030-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a5030-127">Palavras-chave de C#</span><span class="sxs-lookup"><span data-stu-id="a5030-127">C# keywords</span></span>](index.md)
- [<span data-ttu-id="a5030-128">usando</span><span class="sxs-lookup"><span data-stu-id="a5030-128">using</span></span>](using-directive.md)
- [<span data-ttu-id="a5030-129">usando estático</span><span class="sxs-lookup"><span data-stu-id="a5030-129">using static</span></span>](using-static.md)
- [<span data-ttu-id="a5030-130">Qualificador de alias de namespace `::`</span><span class="sxs-lookup"><span data-stu-id="a5030-130">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="a5030-131">Namespaces</span><span class="sxs-lookup"><span data-stu-id="a5030-131">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
