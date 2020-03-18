---
title: Propriedades autoimplementadas – Guia de Programação em C#
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 791455c1eaef752da2b551e20187d390ca6c65e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170319"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="d3f75-102">Propriedades autoimplementadas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d3f75-102">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="d3f75-103">No C# 3.0 e versões posteriores, as propriedades autoimplementadas tornam a declaração de propriedade mais concisa quando nenhuma lógica adicional for necessária nos acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d3f75-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="d3f75-104">Elas também habilitam o código do cliente a criar objetos.</span><span class="sxs-lookup"><span data-stu-id="d3f75-104">They also enable client code to create objects.</span></span> <span data-ttu-id="d3f75-105">Ao declarar uma propriedade, como mostrado no exemplo a seguir, o compilador cria um campo de suporte privado e anônimo que pode ser acessado somente por meio dos acessadores `get` e `set` da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d3f75-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="d3f75-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3f75-106">Example</span></span>

<span data-ttu-id="d3f75-107">O exemplo a seguir mostra uma classe simples que tem algumas propriedades autoimplementadas:</span><span class="sxs-lookup"><span data-stu-id="d3f75-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="d3f75-108">Você não pode declarar propriedades implementadas automaticamente em interfaces.</span><span class="sxs-lookup"><span data-stu-id="d3f75-108">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="d3f75-109">Propriedades implementadas automaticamente declaram um campo de backup de instância privada e as interfaces não podem declarar campos de ocorrência.</span><span class="sxs-lookup"><span data-stu-id="d3f75-109">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="d3f75-110">Declarar uma propriedade em uma interface sem definir um corpo declara uma propriedade com acessórios que devem ser implementados por cada tipo que implementa essa interface.</span><span class="sxs-lookup"><span data-stu-id="d3f75-110">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="d3f75-111">No C# 6 e versões posteriores, é possível inicializar as propriedades autoimplementadas da mesma forma que os campos:</span><span class="sxs-lookup"><span data-stu-id="d3f75-111">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="d3f75-112">A classe mostrada no exemplo anterior é mutável.</span><span class="sxs-lookup"><span data-stu-id="d3f75-112">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="d3f75-113">O código do cliente pode alterar os valores em objetos após a criação.</span><span class="sxs-lookup"><span data-stu-id="d3f75-113">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="d3f75-114">Em classes complexas que contêm comportamentos significativos (métodos) e dados, muitas vezes é necessário ter propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="d3f75-114">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="d3f75-115">No entanto, para classes pequenas ou structs que apenas encapsulam um conjunto de valores (dados) e têm poucos ou nenhum comportamento, faça com que os objetos se tornem imutáveis declarando o acessador set como [privado](../../language-reference/keywords/private.md) (imutável para consumidores) ou declarando somente um acessador get (imutável em todos os lugares, exceto no construtor).</span><span class="sxs-lookup"><span data-stu-id="d3f75-115">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="d3f75-116">Para obter mais informações, consulte [Como implementar uma classe leve com propriedades auto-implementadas.](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)</span><span class="sxs-lookup"><span data-stu-id="d3f75-116">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d3f75-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="d3f75-117">See also</span></span>

- [<span data-ttu-id="d3f75-118">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d3f75-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="d3f75-119">Modificadores</span><span class="sxs-lookup"><span data-stu-id="d3f75-119">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
