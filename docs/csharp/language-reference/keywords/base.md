---
title: "base (Referência de C#)"
description: "Saiba mais sobre a palavra-chave base, que é usada para acessar membros da classe base de dentro de uma classe derivada em C#."
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
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
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: b3a389d92373b6ba5995a7644b0440f9d8fad9ac
ms.contentlocale: pt-br
ms.lasthandoff: 08/17/2017

---
# <a name="base-c-reference"></a><span data-ttu-id="270aa-103">base (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="270aa-103">base (C# Reference)</span></span>

<span data-ttu-id="270aa-104">A palavra-chave `base` é usada para acessar membros de classe base de dentro de uma classe derivada:</span><span class="sxs-lookup"><span data-stu-id="270aa-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="270aa-105">Chamar um método que foi substituído por outro método na classe base.</span><span class="sxs-lookup"><span data-stu-id="270aa-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="270aa-106">Especificar qual construtor de classe base deve ser chamado ao criar instâncias da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="270aa-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="270aa-107">Um acesso de classe base é permitido somente em um construtor, em um método de instância ou em um acessador de propriedade de instância.</span><span class="sxs-lookup"><span data-stu-id="270aa-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="270aa-108">É um erro usar a palavra-chave `base` de dentro de um método estático.</span><span class="sxs-lookup"><span data-stu-id="270aa-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="270aa-109">A classe base que é acessada é a que é especificada na declaração de classe.</span><span class="sxs-lookup"><span data-stu-id="270aa-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="270aa-110">Por exemplo, se você especificar `class ClassB : ClassA`, os membros da ClassA são acessados da ClassB, independentemente da classe base da ClassA.</span><span class="sxs-lookup"><span data-stu-id="270aa-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="270aa-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="270aa-111">Example</span></span>
<span data-ttu-id="270aa-112">Neste exemplo, as classes base `Person` e a classe derivada `Employee` têm um método chamado `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="270aa-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="270aa-113">Usando a palavra-chave `base`, é possível chamar o método `Getinfo` na classe base, de dentro da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="270aa-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

<span data-ttu-id="270aa-114">[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="270aa-114">[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]</span></span>

<span data-ttu-id="270aa-115">Para obter exemplos adicionais, consulte [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md) e [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="270aa-115">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="270aa-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="270aa-116">Example</span></span>
<span data-ttu-id="270aa-117">Este exemplo mostra como especificar o construtor da classe base chamado ao criar instâncias de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="270aa-117">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

<span data-ttu-id="270aa-118">[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="270aa-118">[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="270aa-119">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="270aa-119">C# language specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="270aa-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="270aa-120">See also</span></span>
 <span data-ttu-id="270aa-121">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="270aa-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="270aa-122">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="270aa-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="270aa-123">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="270aa-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="270aa-124">this</span><span class="sxs-lookup"><span data-stu-id="270aa-124">this</span></span>](../../../csharp/language-reference/keywords/this.md)
