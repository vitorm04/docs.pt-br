---
title: Como declarar e usar as propriedades de leitura/gravação – guia de programação em C#
description: Saiba como usar as propriedades de leitura/gravação em C#. Este exemplo inclui duas propriedades, cada uma das quais tem acessadores get e Set, para que as propriedades sejam de leitura/gravação.
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: a2bfc3f43db84ebf69f9a5f41c118c5981e33c19
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199140"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="b0f0c-104">Como declarar e usar propriedades de leitura/gravação (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="b0f0c-104">How to declare and use read write properties (C# Programming Guide)</span></span>

<span data-ttu-id="b0f0c-105">As propriedades oferecem a conveniência de membros de dados públicos sem os riscos associados ao acesso sem proteção, sem controle e não verificado aos dados de um objeto.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-105">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="b0f0c-106">Isso é feito por meio de *acessadores*: métodos especiais que atribuem e recuperam valores do membro de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-106">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="b0f0c-107">O acessador [set](../../language-reference/keywords/set.md) habilita a atribuição de membros de dados e o acessador [get](../../language-reference/keywords/get.md) recupera valores do membro de dados.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-107">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="b0f0c-108">Este exemplo mostra uma classe `Person` que tem duas propriedades: `Name` (string) e `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="b0f0c-108">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="b0f0c-109">Ambas as propriedades fornecem acessadores `get` e `set`, portanto, são consideradas propriedades de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-109">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0f0c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0f0c-110">Example</span></span>  

 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b0f0c-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b0f0c-111">Robust Programming</span></span>  

 <span data-ttu-id="b0f0c-112">No exemplo anterior, as propriedades `Name` e `Age` são [públicas](../../language-reference/keywords/public.md) e incluem os acessadores `get` e `set`.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-112">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="b0f0c-113">Isso permite que qualquer objeto leia e grave essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-113">This allows any object to read and write these properties.</span></span> <span data-ttu-id="b0f0c-114">No entanto, às vezes é desejável excluir um os acessadores.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-114">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="b0f0c-115">Omitir o acessador `set`, por exemplo, torna a propriedade somente leitura:</span><span class="sxs-lookup"><span data-stu-id="b0f0c-115">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="b0f0c-116">Como alternativa, é possível expor um acessador publicamente, porém, tornando o outro privado ou protegido.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-116">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="b0f0c-117">Para obter mais informações, consulte [Acessibilidade do Acessador Assimétrico](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="b0f0c-117">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="b0f0c-118">Depois de serem declaradas, as propriedades podem ser usadas como campos da classe.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-118">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="b0f0c-119">Isso permite uma sintaxe muito natural na obtenção e configuração do valor de uma propriedade, conforme as instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="b0f0c-119">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="b0f0c-120">Observe que em um método de propriedade `set`, uma variável especial `value` está disponível.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-120">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="b0f0c-121">Essa variável contém o valor que o usuário especificou, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b0f0c-121">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="b0f0c-122">Observe a sintaxe normal para incrementar a propriedade `Age` em um objeto `Person`:</span><span class="sxs-lookup"><span data-stu-id="b0f0c-122">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="b0f0c-123">Se métodos `set` e `get` separados fossem usados para modelar propriedades, o código equivalente se pareceria com isto:</span><span class="sxs-lookup"><span data-stu-id="b0f0c-123">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="b0f0c-124">O método `ToString` é substituído neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="b0f0c-124">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="b0f0c-125">Observe que `ToString` não é usado explicitamente no programa.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-125">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="b0f0c-126">Ele é invocado por padrão pelas chamadas `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="b0f0c-126">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f0c-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="b0f0c-127">See also</span></span>

- [<span data-ttu-id="b0f0c-128">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b0f0c-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b0f0c-129">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b0f0c-129">Properties</span></span>](./properties.md)
- [<span data-ttu-id="b0f0c-130">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="b0f0c-130">Classes and Structs</span></span>](./index.md)
