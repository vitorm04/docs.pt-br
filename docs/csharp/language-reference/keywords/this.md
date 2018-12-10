---
title: Palavra-chave this (Referência de C#)
description: Palavra-chave this (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 52e7fce0ebeeccfbf5f56dbbcade9fae2890dfe1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130803"
---
# <a name="this-c-reference"></a><span data-ttu-id="ce6ce-103">this (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ce6ce-103">this (C# Reference)</span></span>

<span data-ttu-id="ce6ce-104">A palavra-chave `this` refere-se à instância atual da classe e também é usada como um modificador do primeiro parâmetro de um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="ce6ce-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="ce6ce-105">Este artigo discute o uso de `this` com instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="ce6ce-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="ce6ce-106">Para obter mais informações sobre seu uso em métodos de extensão, consulte [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ce6ce-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="ce6ce-107">Veja a seguir usos comuns de `this`:</span><span class="sxs-lookup"><span data-stu-id="ce6ce-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="ce6ce-108">Para qualificar membros ocultados por nomes semelhantes, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ce6ce-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="ce6ce-109">Para passar um objeto como parâmetro para outros métodos, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ce6ce-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="ce6ce-110">Para declarar indexadores, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ce6ce-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="ce6ce-111">Funções de membro estático, por existirem no nível da classe e não como parte de um objeto, não têm um ponteiro `this`.</span><span class="sxs-lookup"><span data-stu-id="ce6ce-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="ce6ce-112">É um erro se referir a `this` em um método estático.</span><span class="sxs-lookup"><span data-stu-id="ce6ce-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="ce6ce-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce6ce-113">Example</span></span>

<span data-ttu-id="ce6ce-114">Neste exemplo, `this` é usado para qualificar os membros de classe `Employee`, `name` e `alias`, que são ocultados por nomes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="ce6ce-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="ce6ce-115">Ele também é usado para passar um objeto para o método `CalcTax`, que pertence a outra classe.</span><span class="sxs-lookup"><span data-stu-id="ce6ce-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="ce6ce-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ce6ce-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ce6ce-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce6ce-117">See also</span></span>

- [<span data-ttu-id="ce6ce-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ce6ce-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ce6ce-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ce6ce-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ce6ce-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="ce6ce-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ce6ce-121">base</span><span class="sxs-lookup"><span data-stu-id="ce6ce-121">base</span></span>](base.md)
- [<span data-ttu-id="ce6ce-122">Métodos</span><span class="sxs-lookup"><span data-stu-id="ce6ce-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
