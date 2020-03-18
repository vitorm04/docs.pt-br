---
title: Delegados em C# - um tour pela linguagem C#
description: Aprenda a associação tardia com delegados C#
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159163"
---
# <a name="delegates"></a><span data-ttu-id="3b917-103">Delega</span><span class="sxs-lookup"><span data-stu-id="3b917-103">Delegates</span></span>

<span data-ttu-id="3b917-104">Um ***delegado*** é um tipo que representa referências aos métodos com uma lista de parâmetros e tipo de retorno específicos.</span><span class="sxs-lookup"><span data-stu-id="3b917-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="3b917-105">Delegados possibilitam o tratamento de métodos como entidades que podem ser atribuídos a variáveis e passadas como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3b917-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="3b917-106">Os delegados são semelhantes ao conceito de ponteiros de função encontrados em algumas outras línguas.</span><span class="sxs-lookup"><span data-stu-id="3b917-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="3b917-107">Ao contrário dos ponteiros de função, os delegados são orientados a objetos e seguros para o tipo.</span><span class="sxs-lookup"><span data-stu-id="3b917-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="3b917-108">O exemplo a seguir declara e usa um tipo delegado chamado `Function`.</span><span class="sxs-lookup"><span data-stu-id="3b917-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="3b917-109">Uma instância do tipo delegado `Function` pode fazer referência a qualquer método que usa um argumento `double` e retorna um valor `double`.</span><span class="sxs-lookup"><span data-stu-id="3b917-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="3b917-110">O método `Apply` aplica uma determinada função aos elementos de um `double[]`, retornando um `double[]` com os resultados.</span><span class="sxs-lookup"><span data-stu-id="3b917-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="3b917-111">No método `Main`, `Apply` é usado para aplicar três funções diferentes para um `double[]`.</span><span class="sxs-lookup"><span data-stu-id="3b917-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="3b917-112">Um delegado pode referenciar um método estático (como `Square` ou `Math.Sin` no exemplo anterior) ou um método de instância (como `m.Multiply` no exemplo anterior).</span><span class="sxs-lookup"><span data-stu-id="3b917-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="3b917-113">Um delegado que referencia um método de instância também referencia um objeto específico, e quando o método de instância é invocado por meio do delegado, esse objeto se torna `this` na invocação.</span><span class="sxs-lookup"><span data-stu-id="3b917-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="3b917-114">Os delegados também podem ser criados usando funções anônimas, que são "métodos inline" que são criados quando declarados.</span><span class="sxs-lookup"><span data-stu-id="3b917-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="3b917-115">As funções anônimas podem ver as variáveis locais dos métodos ao redor.</span><span class="sxs-lookup"><span data-stu-id="3b917-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="3b917-116">O exemplo a seguir não cria uma classe:</span><span class="sxs-lookup"><span data-stu-id="3b917-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="3b917-117">Um delegado não sabe ou se preocupa com a classe do método que ele se refere; tudo o que importa é que o método referenciado tem os mesmos parâmetros e tipo de retorno que o delegado.</span><span class="sxs-lookup"><span data-stu-id="3b917-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3b917-118">[Próximo](interfaces.md)
>[anterior](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="3b917-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
