---
title: this (Referência de C#)
description: Palavra-chave this (Referência de C#)
keywords: this (C#), palavra-chave this (C#), palavra-chave this (referência de C#), palavra-chave this (referência da linguagem C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a><span data-ttu-id="198f3-104">this (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="198f3-104">this (C# Reference)</span></span>
<span data-ttu-id="198f3-105">A palavra-chave `this` refere-se à instância atual da classe e também é usada como um modificador do primeiro parâmetro de um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="198f3-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="198f3-106">Este artigo discute o uso de `this` com instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="198f3-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="198f3-107">Para obter mais informações sobre seu uso em métodos de extensão, consulte [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="198f3-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="198f3-108">Veja a seguir usos comuns de `this`:</span><span class="sxs-lookup"><span data-stu-id="198f3-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="198f3-109">Para qualificar membros ocultados por nomes semelhantes, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="198f3-109">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="198f3-110">Para passar um objeto como parâmetro para outros métodos, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="198f3-110">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="198f3-111">Para declarar indexadores, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="198f3-111">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="198f3-112">Funções de membro estático, por existirem no nível da classe e não como parte de um objeto, não têm um ponteiro `this`.</span><span class="sxs-lookup"><span data-stu-id="198f3-112">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="198f3-113">É um erro se referir a `this` em um método estático.</span><span class="sxs-lookup"><span data-stu-id="198f3-113">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="198f3-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="198f3-114">Example</span></span>  
 <span data-ttu-id="198f3-115">Neste exemplo, `this` é usado para qualificar os membros de classe `Employee`, `name` e `alias`, que são ocultados por nomes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="198f3-115">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="198f3-116">Ele também é usado para passar um objeto para o método `CalcTax`, que pertence a outra classe.</span><span class="sxs-lookup"><span data-stu-id="198f3-116">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="198f3-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="198f3-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="198f3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="198f3-118">See Also</span></span>  
 [<span data-ttu-id="198f3-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="198f3-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="198f3-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="198f3-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="198f3-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="198f3-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="198f3-122">base</span><span class="sxs-lookup"><span data-stu-id="198f3-122">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="198f3-123">Métodos</span><span class="sxs-lookup"><span data-stu-id="198f3-123">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
