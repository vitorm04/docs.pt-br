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
ms.openlocfilehash: 04595e96f6f14b8806a2d89625151910cac9e0d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345415"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="a787f-102">namespace (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a787f-102">namespace (C# Reference)</span></span>

<span data-ttu-id="a787f-103">A palavra-chave `namespace` é usada para declarar um escopo que contém um conjunto de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="a787f-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="a787f-104">Você pode usar um namespace para organizar elementos de código e criar tipos globalmente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="a787f-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="a787f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a787f-105">Remarks</span></span>

<span data-ttu-id="a787f-106">Dentro de um namespace, é possível declarar zero ou mais dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="a787f-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="a787f-107">outro namespace</span><span class="sxs-lookup"><span data-stu-id="a787f-107">another namespace</span></span>

- [<span data-ttu-id="a787f-108">class</span><span class="sxs-lookup"><span data-stu-id="a787f-108">class</span></span>](class.md)

- [<span data-ttu-id="a787f-109">interface</span><span class="sxs-lookup"><span data-stu-id="a787f-109">interface</span></span>](interface.md)

- [<span data-ttu-id="a787f-110">struct</span><span class="sxs-lookup"><span data-stu-id="a787f-110">struct</span></span>](struct.md)

- [<span data-ttu-id="a787f-111">enum</span><span class="sxs-lookup"><span data-stu-id="a787f-111">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="a787f-112">delegate</span><span class="sxs-lookup"><span data-stu-id="a787f-112">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="a787f-113">Quer você declare explicitamente ou não um namespace em um arquivo de origem C#, o compilador adiciona um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="a787f-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="a787f-114">Este namespace sem nome, às vezes chamado de namespace global, está presente em todos os arquivos.</span><span class="sxs-lookup"><span data-stu-id="a787f-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="a787f-115">Qualquer identificador no namespace global está disponível para uso em um namespace nomeado.</span><span class="sxs-lookup"><span data-stu-id="a787f-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="a787f-116">Os namespaces implicitamente têm acesso público e não isso é modificável.</span><span class="sxs-lookup"><span data-stu-id="a787f-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="a787f-117">Para uma discussão sobre os modificadores de acesso que você pode atribuir a elementos em um namespace, consulte [Modificadores de acesso](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="a787f-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="a787f-118">É possível definir um namespace em duas ou mais declarações.</span><span class="sxs-lookup"><span data-stu-id="a787f-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="a787f-119">Por exemplo, o exemplo a seguir define duas classes como parte do namespace `MyCompany`:</span><span class="sxs-lookup"><span data-stu-id="a787f-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="a787f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a787f-120">Example</span></span>

<span data-ttu-id="a787f-121">O exemplo a seguir mostra como chamar um método estático em um namespace aninhado.</span><span class="sxs-lookup"><span data-stu-id="a787f-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="a787f-122">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a787f-122">C# language specification</span></span>

<span data-ttu-id="a787f-123">Para saber mais, confira a seção [Namespaces](~/_csharplang/spec/namespaces.md) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a787f-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a787f-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="a787f-124">See also</span></span>

- [<span data-ttu-id="a787f-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a787f-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a787f-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a787f-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="a787f-127">using</span><span class="sxs-lookup"><span data-stu-id="a787f-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="a787f-128">using static</span><span class="sxs-lookup"><span data-stu-id="a787f-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="a787f-129">Qualificador de alias de namespace `::`</span><span class="sxs-lookup"><span data-stu-id="a787f-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="a787f-130">Namespaces</span><span class="sxs-lookup"><span data-stu-id="a787f-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
