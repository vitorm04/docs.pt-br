---
title: "Como Declarar e Usar Propriedades de Leitura e Gravação (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e5e4ca1feff203dc2ab88c0d1dfae8098508fec7
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="2759f-102">Como Declarar e Usar Propriedades de Leitura e Gravação (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2759f-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="2759f-103">As propriedades oferecem a conveniência de membros de dados públicos sem os riscos associados ao acesso sem proteção, sem controle e não verificado aos dados de um objeto.</span><span class="sxs-lookup"><span data-stu-id="2759f-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="2759f-104">Isso é feito por meio de *acessadores*: métodos especiais que atribuem e recuperam valores do membro de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="2759f-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="2759f-105">O acessador [set](../../../csharp/language-reference/keywords/set.md) habilita a atribuição de membros de dados e o acessador [get](../../../csharp/language-reference/keywords/get.md) recupera valores do membro de dados.</span><span class="sxs-lookup"><span data-stu-id="2759f-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="2759f-106">Este exemplo mostra uma classe `Person` que tem duas propriedades: `Name` (string) e `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="2759f-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="2759f-107">Ambas as propriedades fornecem acessadores `get` e `set`, portanto, são consideradas propriedades de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="2759f-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2759f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2759f-108">Example</span></span>  
 <span data-ttu-id="2759f-109">[!code-cs[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2759f-109">[!code-cs[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2759f-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="2759f-110">Robust Programming</span></span>  
 <span data-ttu-id="2759f-111">No exemplo anterior, as propriedades `Name` e `Age` são [públicas](../../../csharp/language-reference/keywords/public.md) e incluem os acessadores `get` e `set`.</span><span class="sxs-lookup"><span data-stu-id="2759f-111">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="2759f-112">Isso permite que qualquer objeto leia e grave essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="2759f-112">This allows any object to read and write these properties.</span></span> <span data-ttu-id="2759f-113">No entanto, às vezes é desejável excluir um os acessadores.</span><span class="sxs-lookup"><span data-stu-id="2759f-113">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="2759f-114">Omitir o acessador `set`, por exemplo, torna a propriedade somente leitura:</span><span class="sxs-lookup"><span data-stu-id="2759f-114">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 <span data-ttu-id="2759f-115">[!code-cs[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2759f-115">[!code-cs[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]</span></span>  
  
 <span data-ttu-id="2759f-116">Como alternativa, é possível expor um acessador publicamente, porém, tornando o outro privado ou protegido.</span><span class="sxs-lookup"><span data-stu-id="2759f-116">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="2759f-117">Para obter mais informações, consulte [Acessibilidade do Acessador Assimétrico](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="2759f-117">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="2759f-118">Depois de serem declaradas, as propriedades podem ser usadas como campos da classe.</span><span class="sxs-lookup"><span data-stu-id="2759f-118">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="2759f-119">Isso permite uma sintaxe muito natural na obtenção e configuração do valor de uma propriedade, conforme as instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="2759f-119">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 <span data-ttu-id="2759f-120">[!code-cs[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2759f-120">[!code-cs[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]</span></span>  
  
 <span data-ttu-id="2759f-121">Observe que em um método de propriedade `set`, uma variável especial `value` está disponível.</span><span class="sxs-lookup"><span data-stu-id="2759f-121">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="2759f-122">Essa variável contém o valor que o usuário especificou, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2759f-122">This variable contains the value that the user specified, for example:</span></span>  
  
 <span data-ttu-id="2759f-123">[!code-cs[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="2759f-123">[!code-cs[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]</span></span>  
  
 <span data-ttu-id="2759f-124">Observe a sintaxe normal para incrementar a propriedade `Age` em um objeto `Person`:</span><span class="sxs-lookup"><span data-stu-id="2759f-124">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 <span data-ttu-id="2759f-125">[!code-cs[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="2759f-125">[!code-cs[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]</span></span>  
  
 <span data-ttu-id="2759f-126">Se métodos `set` e `get` separados fossem usados para modelar propriedades, o código equivalente se pareceria com isto:</span><span class="sxs-lookup"><span data-stu-id="2759f-126">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="2759f-127">O método `ToString` é substituído neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="2759f-127">The `ToString` method is overridden in this example:</span></span>  
  
 <span data-ttu-id="2759f-128">[!code-cs[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="2759f-128">[!code-cs[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]</span></span>  
  
 <span data-ttu-id="2759f-129">Observe que `ToString` não é usado explicitamente no programa.</span><span class="sxs-lookup"><span data-stu-id="2759f-129">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="2759f-130">Ele é invocado por padrão pelas chamadas `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="2759f-130">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2759f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2759f-131">See Also</span></span>  
 <span data-ttu-id="2759f-132">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2759f-132">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2759f-133">[Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="2759f-133">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 [<span data-ttu-id="2759f-134">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="2759f-134">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)

