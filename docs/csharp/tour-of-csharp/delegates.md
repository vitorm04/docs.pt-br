---
title: Delegados em C# - um tour pela linguagem C#
description: Aprenda a associação tardia com delegados C#
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 35a1e212b50e77eb43271a657c8abb21eb6cfb4a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634629"
---
# <a name="delegates"></a><span data-ttu-id="c9b1c-103">Delegados</span><span class="sxs-lookup"><span data-stu-id="c9b1c-103">Delegates</span></span>

<span data-ttu-id="c9b1c-104">Um ***delegado*** é um tipo que representa referências aos métodos com uma lista de parâmetros e tipo de retorno específicos.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="c9b1c-105">Delegados possibilitam o tratamento de métodos como entidades que podem ser atribuídos a variáveis e passadas como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="c9b1c-106">Os delegados são parecidos com o conceito de ponteiros de função em outras linguagens, mas ao contrário dos ponteiros de função, os delegados são orientados a objetos e fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="c9b1c-107">O exemplo a seguir declara e usa um tipo delegado chamado `Function`.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="c9b1c-108">Uma instância do tipo delegado `Function` pode fazer referência a qualquer método que usa um argumento `double` e retorna um valor `double`.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="c9b1c-109">O método `Apply` aplica uma determinada função aos elementos de um `double[]`, retornando um `double[]` com os resultados.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="c9b1c-110">No método `Main`, `Apply` é usado para aplicar três funções diferentes para um `double[]`.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="c9b1c-111">Um delegado pode referenciar um método estático (como `Square` ou `Math.Sin` no exemplo anterior) ou um método de instância (como `m.Multiply` no exemplo anterior).</span><span class="sxs-lookup"><span data-stu-id="c9b1c-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="c9b1c-112">Um delegado que referencia um método de instância também referencia um objeto específico, e quando o método de instância é invocado por meio do delegado, esse objeto se torna `this` na invocação.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="c9b1c-113">Os delegados podem ser criados usando funções anônimas, que são "métodos embutidos" criados dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="c9b1c-114">As funções anônimas podem ver as variáveis locais dos métodos ao redor.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="c9b1c-115">Assim, o exemplo de multiplicador acima pode ser gravado mais facilmente sem usar uma classe de multiplicador:</span><span class="sxs-lookup"><span data-stu-id="c9b1c-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="c9b1c-116">Uma propriedade interessante e útil de um delegado é que ele não sabe ou se importa com a classe do método que referencia; o que importa é que o método referenciado tem os mesmos parâmetros e o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="c9b1c-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c9b1c-117">[Anterior](enums.md)
>[Próximo](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="c9b1c-117">[Previous](enums.md)
[Next](attributes.md)</span></span>
