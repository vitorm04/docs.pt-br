---
title: palavra-chave de base (Referência de C#)
description: Saiba mais sobre a palavra-chave base, que é usada para acessar membros da classe base de dentro de uma classe derivada em C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713764"
---
# <a name="base-c-reference"></a><span data-ttu-id="eefeb-103">base (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="eefeb-103">base (C# Reference)</span></span>

<span data-ttu-id="eefeb-104">A palavra-chave `base` é usada para acessar membros de classe base de dentro de uma classe derivada:</span><span class="sxs-lookup"><span data-stu-id="eefeb-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="eefeb-105">Chamar um método que foi substituído por outro método na classe base.</span><span class="sxs-lookup"><span data-stu-id="eefeb-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="eefeb-106">Especificar qual construtor de classe base deve ser chamado ao criar instâncias da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="eefeb-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="eefeb-107">Um acesso de classe base é permitido somente em um construtor, em um método de instância ou em um acessador de propriedade de instância.</span><span class="sxs-lookup"><span data-stu-id="eefeb-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="eefeb-108">É um erro usar a palavra-chave `base` de dentro de um método estático.</span><span class="sxs-lookup"><span data-stu-id="eefeb-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="eefeb-109">A classe base que é acessada é a que é especificada na declaração de classe.</span><span class="sxs-lookup"><span data-stu-id="eefeb-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="eefeb-110">Por exemplo, se você especificar `class ClassB : ClassA`, os membros da ClassA são acessados da ClassB, independentemente da classe base da ClassA.</span><span class="sxs-lookup"><span data-stu-id="eefeb-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="eefeb-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eefeb-111">Example</span></span>

<span data-ttu-id="eefeb-112">Neste exemplo, as classes base `Person` e a classe derivada `Employee` têm um método chamado `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="eefeb-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="eefeb-113">Usando a palavra-chave `base`, é possível chamar o método `Getinfo` na classe base, de dentro da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="eefeb-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

<span data-ttu-id="eefeb-114">Para obter exemplos adicionais, consulte [new](new-modifier.md), [virtual](virtual.md) e [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="eefeb-114">For additional examples, see [new](new-modifier.md), [virtual](virtual.md), and [override](override.md).</span></span>

## <a name="example"></a><span data-ttu-id="eefeb-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eefeb-115">Example</span></span>

<span data-ttu-id="eefeb-116">Este exemplo mostra como especificar o construtor da classe base chamado ao criar instâncias de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="eefeb-116">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="eefeb-117">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="eefeb-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="eefeb-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="eefeb-118">See also</span></span>

- [<span data-ttu-id="eefeb-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="eefeb-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eefeb-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="eefeb-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eefeb-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="eefeb-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="eefeb-122">this</span><span class="sxs-lookup"><span data-stu-id="eefeb-122">this</span></span>](./this.md)
