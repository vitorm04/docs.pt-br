---
title: Propriedades autoimplementadas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 6768926c782b23dd495b338125d62b7833b0d9e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554511"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="ecb9e-102">Propriedades autoimplementadas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ecb9e-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="ecb9e-103">No C# 3.0 e versões posteriores, as propriedades autoimplementadas tornam a declaração de propriedade mais concisa quando nenhuma lógica adicional for necessária nos acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="ecb9e-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="ecb9e-104">Elas também habilitam o código do cliente a criar objetos.</span><span class="sxs-lookup"><span data-stu-id="ecb9e-104">They also enable client code to create objects.</span></span> <span data-ttu-id="ecb9e-105">Ao declarar uma propriedade, como mostrado no exemplo a seguir, o compilador cria um campo de suporte privado e anônimo que pode ser acessado somente por meio dos acessadores `get` e `set` da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ecb9e-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecb9e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ecb9e-106">Example</span></span>  
 <span data-ttu-id="ecb9e-107">O exemplo a seguir mostra uma classe simples que tem algumas propriedades autoimplementadas:</span><span class="sxs-lookup"><span data-stu-id="ecb9e-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="ecb9e-108">No C# 6 e versões posteriores, é possível inicializar as propriedades autoimplementadas da mesma forma que os campos:</span><span class="sxs-lookup"><span data-stu-id="ecb9e-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="ecb9e-109">A classe mostrada no exemplo anterior é mutável.</span><span class="sxs-lookup"><span data-stu-id="ecb9e-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="ecb9e-110">O código cliente pode alterar os valores nos objetos após sua criação.</span><span class="sxs-lookup"><span data-stu-id="ecb9e-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="ecb9e-111">Em classes complexas que contêm comportamento significativo (métodos), bem como dados, geralmente é necessário ter propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="ecb9e-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="ecb9e-112">No entanto, para classes pequenas ou structs que apenas encapsulam um conjunto de valores (dados) e têm poucos ou nenhum comportamento, faça com que os objetos se tornem imutáveis declarando o acessador set como [privado](../../../csharp/language-reference/keywords/private.md) (imutável para consumidores) ou declarando somente um acessador get (imutável em todos os lugares, exceto no construtor).</span><span class="sxs-lookup"><span data-stu-id="ecb9e-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="ecb9e-113">Para obter mais informações, confira [Como: implementar uma classe leve com propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ecb9e-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb9e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecb9e-114">See also</span></span>

- [<span data-ttu-id="ecb9e-115">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ecb9e-115">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="ecb9e-116">Modificadores</span><span class="sxs-lookup"><span data-stu-id="ecb9e-116">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
