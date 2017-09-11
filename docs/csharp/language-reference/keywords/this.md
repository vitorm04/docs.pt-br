---
title: "this (Referência de C#)"
description: "Palavra-chave this (Referência de C#)"
keywords: "this (C#), palavra-chave this (C#), palavra-chave this (referência de C#), palavra-chave this (referência da linguagem C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
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
ms.openlocfilehash: 1e764bbd85d06a3b1898f6574064b2844f6d6813
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="this-c-reference"></a><span data-ttu-id="e41df-104">this (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e41df-104">this (C# Reference)</span></span>
<span data-ttu-id="e41df-105">A palavra-chave `this` refere-se à instância atual da classe e também é usada como um modificador do primeiro parâmetro de um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="e41df-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e41df-106">Este artigo discute o uso de `this` com instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="e41df-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="e41df-107">Para obter mais informações sobre seu uso em métodos de extensão, consulte [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e41df-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="e41df-108">Veja a seguir usos comuns de `this`:</span><span class="sxs-lookup"><span data-stu-id="e41df-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="e41df-109">Para qualificar membros ocultados por nomes semelhantes, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e41df-109">To qualify members hidden by similar names, for example:</span></span>  
  
 <span data-ttu-id="e41df-110">[!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e41df-110">[!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]</span></span>  
  
-   <span data-ttu-id="e41df-111">Para passar um objeto como parâmetro para outros métodos, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e41df-111">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="e41df-112">Para declarar indexadores, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e41df-112">To declare indexers, for example:</span></span>  
  
 <span data-ttu-id="e41df-113">[!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e41df-113">[!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]</span></span>  
  
 <span data-ttu-id="e41df-114">Funções de membro estático, por existirem no nível da classe e não como parte de um objeto, não têm um ponteiro `this`.</span><span class="sxs-lookup"><span data-stu-id="e41df-114">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="e41df-115">É um erro se referir a `this` em um método estático.</span><span class="sxs-lookup"><span data-stu-id="e41df-115">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e41df-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e41df-116">Example</span></span>  
 <span data-ttu-id="e41df-117">Neste exemplo, `this` é usado para qualificar os membros de classe `Employee`, `name` e `alias`, que são ocultados por nomes semelhantes.</span><span class="sxs-lookup"><span data-stu-id="e41df-117">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="e41df-118">Ele também é usado para passar um objeto para o método `CalcTax`, que pertence a outra classe.</span><span class="sxs-lookup"><span data-stu-id="e41df-118">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 <span data-ttu-id="e41df-119">[!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="e41df-119">[!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e41df-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e41df-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e41df-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e41df-121">See Also</span></span>  
 <span data-ttu-id="e41df-122">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e41df-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e41df-123">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e41df-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e41df-124">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e41df-124">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="e41df-125">[base](../../../csharp/language-reference/keywords/base.md) </span><span class="sxs-lookup"><span data-stu-id="e41df-125">[base](../../../csharp/language-reference/keywords/base.md) </span></span>  
 [<span data-ttu-id="e41df-126">Métodos</span><span class="sxs-lookup"><span data-stu-id="e41df-126">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

