---
title: Propriedades autoimplementadas – Guia de Programação em C#
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 989266bfc2de9bd5ce2948f09a2b9f19dd2c782e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628287"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="8d92a-102">Propriedades autoimplementadas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8d92a-102">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="8d92a-103">No C# 3.0 e versões posteriores, as propriedades autoimplementadas tornam a declaração de propriedade mais concisa quando nenhuma lógica adicional for necessária nos acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d92a-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="8d92a-104">Elas também habilitam o código do cliente a criar objetos.</span><span class="sxs-lookup"><span data-stu-id="8d92a-104">They also enable client code to create objects.</span></span> <span data-ttu-id="8d92a-105">Ao declarar uma propriedade, como mostrado no exemplo a seguir, o compilador cria um campo de suporte privado e anônimo que pode ser acessado somente por meio dos acessadores `get` e `set` da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d92a-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="8d92a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d92a-106">Example</span></span>

<span data-ttu-id="8d92a-107">O exemplo a seguir mostra uma classe simples que tem algumas propriedades autoimplementadas:</span><span class="sxs-lookup"><span data-stu-id="8d92a-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="8d92a-108">Você não pode declarar Propriedades implementadas automaticamente em interfaces.</span><span class="sxs-lookup"><span data-stu-id="8d92a-108">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="8d92a-109">As propriedades implementadas automaticamente declaram um campo de backup de instância particular, e as interfaces não podem declarar campos de instância.</span><span class="sxs-lookup"><span data-stu-id="8d92a-109">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="8d92a-110">Declarar uma propriedade em uma interface sem definir um corpo declara uma propriedade com acessadores que deve ser implementada por cada tipo que implementa essa interface.</span><span class="sxs-lookup"><span data-stu-id="8d92a-110">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="8d92a-111">No C# 6 e versões posteriores, é possível inicializar as propriedades autoimplementadas da mesma forma que os campos:</span><span class="sxs-lookup"><span data-stu-id="8d92a-111">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
 
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
 
<span data-ttu-id="8d92a-112">A classe mostrada no exemplo anterior é mutável.</span><span class="sxs-lookup"><span data-stu-id="8d92a-112">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="8d92a-113">O código do cliente pode alterar os valores em objetos após a criação.</span><span class="sxs-lookup"><span data-stu-id="8d92a-113">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="8d92a-114">Em classes complexas que contêm comportamento significativo (métodos), bem como dados, geralmente é necessário ter propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="8d92a-114">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="8d92a-115">No entanto, para classes pequenas ou structs que apenas encapsulam um conjunto de valores (dados) e têm poucos ou nenhum comportamento, faça com que os objetos se tornem imutáveis declarando o acessador set como [privado](../../language-reference/keywords/private.md) (imutável para consumidores) ou declarando somente um acessador get (imutável em todos os lugares, exceto no construtor).</span><span class="sxs-lookup"><span data-stu-id="8d92a-115">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="8d92a-116">Para obter mais informações, consulte [como implementar uma classe leve com propriedades implementadas automaticamente](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="8d92a-116">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d92a-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d92a-117">See also</span></span>

- [<span data-ttu-id="8d92a-118">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8d92a-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="8d92a-119">Modificadores</span><span class="sxs-lookup"><span data-stu-id="8d92a-119">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
